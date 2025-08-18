# Introduction to App Builder

This doc is intended to be a spin-up to help developers get up to speed with App Builder and related technologies.

## Target Audience

Technical contributors working with Adobe Developer App Builder and Adobe Commerce inside of Github

## Glossary of Terms (SaaS/ACCS vs PaaS/ACC)

Adobe has made all this super confusing, so here is a glossary of terms to clear things up

**Adobe Commerce as a Cloud Service** or **ACCS** is the new **SaaS** offering by Adobe, internally Blue Acorn and Adobe refer to this as *SaaS* because of it's immutable and API-driven nature that requires developers to follow *Out of Process Extensibility* principles. It is typically paired with *Adobe Commerce Storefront* or some kind of headless frontend. 

**Adobe Commerce Cloud** or **ACC** is the more common traditional **PaaS** offering by Adobe on the white-labled *Platform.sh* service. It's *PaaS* because it takes a platform like *Adobe Commerce* and provides a turn-key service with hosting.  

**Adobe Commerce** is the enterprise eCommerce platform by Adobe, it is a *PHP Application* that can be hosted anywhere. It is a commercial product that requires a license to run and operate, and includes access to **Adobe Developer App Builder** which is the platform by which we can leverage *Out of Process Extensibility* principles to extend the *SaaS* service. 

**Adobe Commerce Storefront** is a presentational "head" for Adobe Commerce, built on *AEM with Edge Delivery Services*, it represents the next generation of performant and scalable storefronts. 

**Edge Delivery Services** or **EDS** is the next-generation hosting and content delivery framework for *Adobe Experience Manager* or *AEM*. It provides the foundation for **Adobe Commerce Storefront** and is designed to resemble a more *statically generated Jamstack* approach.

**Magento Open Source** is a community-driven platform supported by Adobe, is is the *PHP Application* that is the foundation for *Adobe Commerce* and shares most of it's capabilitites. It is not compatibile with *App Builder* and requires *In Process Extensibility*.

**In-Process Extensibility** or **IPE** is a term for traditional PHP development within Adobe Commerce and Magento Opensource. While still standard practice for Magento, Adobe Commerce now expects out-of

**Out-of-Process Extensibility** or **OOPE** refers to techniques for extending capabilitites through new extensibility principles leveraging App Builder in a safer, more scalable manor. This is intended to be the go-forward strategy for Adobe Commerce development.

**Commerce App** refers to any App Builder "app" that is designed for Adobe Commerce, be it by plugging into one of the Out of Process capabilities like Payments, Shipping or Taxes, or by developing something like a Storefront Block which leverages app builder.

**Admin Apps** is a term I will use throughout this guide. It refers to a class of App Builder app that uses the **Admin UI SDK extension points** to present infomration in the Adobe Commerce admin. This is one of the primary use-cases for App Builder.



