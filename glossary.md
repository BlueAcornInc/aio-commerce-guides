# Glossary

Adobe has made all this super confusing, and here at Blue Acorn we have some internal short-hand to add to the confusion. So here is a glossary of terms to clear things up!

**Adobe Commerce as a Cloud Service** or **ACCS** is the new **SaaS** offering by Adobe, internally Blue Acorn and Adobe refer to this as *SaaS* because of it's immutable and API-driven nature that requires developers to follow *Out of Process Extensibility* principles. It is typically paired with *Adobe Commerce Storefront*. 

**Adobe Commerce Cloud** or **ACC** is the more common traditional **PaaS** offering by Adobe on the white-labeled *Platform.sh* service. It's *PaaS* because it takes a platform like *Adobe Commerce* and provides a turn-key service with hosting.  

**Adobe Commerce** is the enterprise eCommerce platform by Adobe, it is a *PHP Application* that can be hosted anywhere. It is a commercial product that requires a license to run and operate, and includes access to **Adobe App Builder** which is the platform by which we can leverage *Out of Process Extensibility* principles to extend the *SaaS* service. 

**Adobe App Builder** Cloud-native development platform on Adobe I/O built on with a common set of tools and patterns to extend Adobe's Enterprise solutions. Adobe App Builder provides capabilities to provide Event-based Out-of-Process Composable Workflows, Custom APIs and even Custom Interfaces as an extension to Adobe's platforms.  Adobe App Builder is the backbone to Adobe's Modern Technology stack powered by Out-of-Process Extensibility. Adobe App Builder is levered with many Adobe Platforms today including Adobe Commerce, AEM, Adobe Experience Platform, Adobe Analytics, Creative Cloud, Marketo, and InDesign.

**Adobe Commerce Storefront** is a presentational "head" for Adobe Commerce, built on *AEM with Edge Delivery Services*, it represents the next generation of performant and scalable storefronts. It's intended to be coupled with Adobe Commerce PaaS or SaaS. 

**Edge Delivery Services** or **EDS** is the next-generation hosting and content delivery framework for *Adobe Experience Manager* or *AEM*. It provides the foundation for **Adobe Commerce Storefront** and is designed to resemble a more *statically generated Jamstack* approach. 

**Adobe Commerce Optimizer** is a separate offering from Adobe Commerce or Storefront, but is complimentary. It's designed to provide front-of-funnel, such as Catalog Indexing and search capabilities, to any ecommerce platform.  It can be paired with *Adobe Commerce Storefront* OOTB and leverage ACC, ACCS or 3rd Party ecommerce platforms as the transactional commerce platform.  **Adobe Commerce Optimizer** is supplied data through Adobe App Builder Integrations which power it's suite of Merchandising Services powered by Channels and Policies, including Product Discovery, Before and After Metrics, API Mesh and an Adobe Commerce Storefront frontend on Edge Delivery.

**Adobe API Mesh** API orchestration layer that unifies APIs from Adobe, third parties, and custom sources.  Allows you to aggregate, and transform responses at the edge, reducing frontend complexity. Enables teams to treat APIs as one consistent, secure endpoint. Supports GraphQL stitching and low-code configuration.  Powerful for enriching data from multiple systems into one unified response for frontend system to consume. 

**EDS/AEM Boilerplate** is a specific repo that has a forkable boilerplate for AEM EDS sites as a base. Sites built with this should be forked from this [AEM Boilerplate repo](https://github.com/adobe/aem-boilerplate)

**EDS/AEM Commerce Boilerplate** A specific fork of tthe EDS with the Commerce Drop-ins and the like. Sites built with this should be forked from this [AEM Commerce Boilerplate repo](https://github.com/hlxsites/aem-boilerplate-commerce), it's likely the right starting point for your SaaS project.

**EDS Commerce Drop-in Components** A specific set of drop-ins for Adobe Commerce Storefornt, here's the general selection [here](https://experienceleague.adobe.com/developer/commerce/storefront/dropins/all/introduction/)

**Document-based Authoring** is a content repository style supported by EDS. This is where content is stored in the form of Documents and Sheets in either Google Drive, Microsoft Sharepoint or Adobe's Document Author. A share link to the content repo is added to the EDS' `fstab.yaml`, this is the default deployment setup for most EDS sites. 

**Code Repository** refers to a Github repo that manages an EDS instance. In the Adobe ecosystem, we delinate between Code and Content repositories, where a code repository can drive many content repositories. 

**Content Repository** refers to any kind of content backend that can provide content and configuration to an EDS site. This includes Document-based authoring, Universal Editor Service, or AEM Classic. 

**Dark Alley** or **Adobe Author** is an Adobe codename for their content repository [da.live](https://da.live/), a content repository for Adobe Edge Delivery Services. **da.live** is where Adobe's starter content is hosted, and can be used to manage content for an EDS site.

**Universal Editor** is an in-context content editor that allows Edge Delivery Services to have a nice drag-and-drop content authoring experience, just like *AEM Classic*.

**Adobe Experience Manager** or **AEM** is an enterprise-grade content management system that is often paired with Adobe Commerce. It's a platform that's been around for decades, and *Edge Delivery Services* is the next generation frontend experience of this platform. Adobe is in the process of re-branding any *EDS* capability as *AEM*. Adobe Experience Manager which includes Sites, Assets, Forms, etc can be integrated with EDS as a content source.

**AEM Classic** is a pejorative referring to traditional forms of AEM, "anything that has a jar file". This includes *AEM as a Cloud Service*, which is a PaaS service to host AEM. Most self-hosted customers use AEM 6.5. AEM is crazy powerful, and most customers at our scale need it's capabilities, but it's our understanding that the Classic flavors will be deprecated eventually for *EDS*, *Universal Editor* and adjacent technologies.  

**Magento Open Source** is a community-driven platform supported by Adobe, is is the *PHP Application* that is the foundation for *Adobe Commerce* and shares most of it's capabilities. It is not compatible with *App Builder* and requires *In-Process Extensibility*.

**Commerce App** refers to any App Builder "app" that is designed for Adobe Commerce, be it by plugging into one of the Out-of-Process capabilities like Payments, Shipping or Taxes, or by developing something like a Storefront Block which leverages app builder.

**Admin Apps** is a term used throughout this guide. It refers to a class of App Builder app that uses the **Adobe Admin UI SDK** to extend the Adobe Commerce on Cloud and Adobe Commerce as a Cloud Service Admin with Out-of-Process Extensibility workflows and customizations to the admin with React Spectrum based UIs, and OOPE event driven workflows. This is one of the primary use-cases for App Builder and Adobe Commerce.

**Out-of-Process Extensibility** or **OOPE** is the recommended approach for extending Adobe Commerce in a scalable, secure, and maintainable way. Instead of modifying the core PHP application directly, developers use **Adobe App Builder** and external services to integrate new capabilities (such as Payments, Shipping, Taxes, or Storefront Blocks). This keeps the Adobe Commerce core immutable, reduces upgrade friction, and promotes modern cloud-native practices. OOPE is intended to be the long-term strategy for Adobe Commerce development, and is required for *SaaS* development. 

**In-Process Extensibility** or **IPE** is the traditional method of extending Adobe Commerce PaaS or Magento Open Source by directly modifying or adding to the core PHP application. This often includes custom modules, plugins, and observers that run within the same process as the platform itself. While still widely used, IPE can introduce upgrade complexity, security risks, and maintenance challenges due to the deep interdependency of modules within the core PHP application. Adobe’s long-term strategy is to reduce reliance on IPE in favor of **Out-of-Process Extensibility (OOPE)**, but it remains necessary for Magento Open Source and some legacy use cases.
