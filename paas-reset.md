# Adobe Commerce Cloud Environment Reset

Here is an incomplete list of commands for resetting an Adobe Commerce Cloud instance with App Builder enablement.

## Reininstall Adobe Commerce

Uninstalling wipes everything down...

```bash
magento-cloud ssh

$ bin/magento uninstall
```

Then perform a deployment to reinstall

## IMS Authentication

Create an App Builder App to house the Oauth Web credential that makes this work

Then perform the following...

```bash
export IMS_ORG_ID=86FF829657DCB10D7F000101@AdobeOrg
export IMS_CLIENT_ID=5e4e02e3795f4ca7aa8807f2793f18f3
export IMS_CLIENT_SECRET=p8e-xxx
export IMS_2FA_ENABLED=yes

bin/magento admin:adobe-ims:enable \
    --organization-id=$IMS_ORG_ID \
    --client-id=$IMS_CLIENT_ID \
    --client-secret=$IMS_CLIENT_SECRET \
    --2fa=$IMS_2FA_ENABLED
```

## Commerce Services Connector

This can be accomplished in the admin by logging in, going to `System` >> `Commerce Services Connector` and completing the steps. 

To automate this...

```bash
config-set-encrypt-file.php services_connector/services_connector_integration/production_private_key $ACSC_PROD_PRIVATE_KEY
n98 config:store:set --encrypt services_connector/services_connector_integration/production_api_key $ACSC_PROD_API_KEY

n98 config:store:set services_connector/services_id/project_id "$ACSC_PROJECT_ID"
n98 config:store:set services_connector/services_id/project_name "$ACSC_PROJECT_NAME"
n98 config:store:set services_connector/services_id/environment_id "$ACSC_ENV_ID"
n98 config:store:set services_connector/services_id/environment_name "$ACSC_ENV_NAME"
n98 config:store:set services_connector/services_id/environment "$ACSC_ENV"

n98 config:store:set admin_ui_sdk/general_config/selected_workspace "$ACSC_WORKSPACE"
n98 config:store:set admin_ui_sdk/general_config/enable_admin_ui_sdk 1
```

Please note that saving encrypted files is not supported yet, so you can use the [config-set-encrypt-file.php](https://github.com/BlueAcornInc/adobe-commerce/blob/production/.devcontainer/bin/config-set-encrypt-file.php) bash script to facilitate. This is handled in the admin when you set it up that way!

## Fastly VCL Updates

```bash
export FASTLY_SERVICE_ID=$(bin/magento config:show system/full_page_cache/fastly/fastly_service_id)
export FASTLY_API_TOKEN=$(bin/magento config:show system/full_page_cache/fastly/fastly_api_key)


export FASTLY_VERSION_ACTIVE=$(curl -H "Fastly-Key: $FASTLY_API_TOKEN" https://api.fastly.com/service/$FASTLY_SERVICE_ID/version/active | jq .number) 

export FASTLY_EDIT_VERSION=$(curl -H "Fastly-Key: $FASTLY_API_TOKEN" https://api.fastly.com/service/$FASTLY_SERVICE_ID/version/$FASTLY_VERSION_ACTIVE/clone -X PUT | jq .number)


curl -H "Fastly-Key: $FASTLY_API_TOKEN" https://api.fastly.com/service/$FASTLY_SERVICE_ID/version/active # Get Active Version


curl -H "Fastly-Key: $FASTLY_API_TOKEN" https://api.fastly.com/service/$FASTLY_SERVICE_ID/version/$FASTLY_VERSION_ACTIVE/clone -X PUT # Clone the active version

curl -H "Fastly-Key: $FASTLY_API_TOKEN" https://api.fastly.com/service/$FASTLY_SERVICE_ID/version/$FASTLY_EDIT_VERSION/snippet/magentomodule_csp_medallia_staging # Fetches a VCL Snippet 

curl -H "Fastly-Key: $FASTLY_API_TOKEN" https://api.fastly.com/service/$FASTLY_SERVICE_ID/version/$FASTLY_EDIT_VERSION/snippet/magentomodule_csp_medallia_staging -X DELETE # Deletes the Snippet

curl -H "Fastly-Key: $FASTLY_API_TOKEN" https://api.fastly.com/service/$FASTLY_SERVICE_ID/version/$FASTLY_EDIT_VERSION/validate # Validate the change you just made

curl -H "Fastly-Key: $FASTLY_API_TOKEN" https://api.fastly.com/service/$FASTLY_SERVICE_ID/version/$FASTLY_EDIT_VERSION/activate -X PUT # Activate the change

curl -H "Fastly-Key: $FASTLY_API_TOKEN" https://api.fastly.com/service/$FASTLY_SERVICE_ID/version/$FASTLY_EDIT_VERSION/validate # validate again!
```

# Commerce Integration Sync

```bash
bin/magento saas:resync --feed productattributes --cleanup-feed
bin/magento saas:resync --feed products --cleanup-feed
bin/magento saas:resync --feed scopesCustomerGroup --cleanup-feed
bin/magento saas:resync --feed scopesWebsite --cleanup-feed
bin/magento saas:resync --feed prices --cleanup-feed
bin/magento saas:resync --feed productoverrides --cleanup-feed
bin/magento saas:resync --feed variants --cleanup-feed
bin/magento saas:resync --feed categories --cleanup-feed
bin/magento saas:resync --feed categoryPermissions --cleanup-feed
```