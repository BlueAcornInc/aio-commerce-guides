# Glossary

Adobe has made all this super confusing, and here at Blue Acorn we have some internal short-hand to add to the confusion. So here is a glossary of terms to clear things up!

**Adobe Commerce as a Cloud Service** or **ACCS** is the new **SaaS** offering by Adobe, internally Blue Acorn and Adobe refer to this as *SaaS* because of it's immutable and API-driven nature that requires developers to follow *Out of Process Extensibility* principles. It is typically paired with *Adobe Commerce Storefront* or some kind of headless frontend. 

**Adobe Commerce Cloud** or **ACC** is the more common traditional **PaaS** offering by Adobe on the white-labled *Platform.sh* service. It's *PaaS* because it takes a platform like *Adobe Commerce* and provides a turn-key service with hosting.  

**Adobe Commerce** is the enterprise eCommerce platform by Adobe, it is a *PHP Application* that can be hosted anywhere. It is a commercial product that requires a license to run and operate, and includes access to **Adobe Developer App Builder** which is the platform by which we can leverage *Out of Process Extensibility* principles to extend the *SaaS* service. 

**Adobe Commerce Storefront** is a presentational "head" for Adobe Commerce, built on *AEM with Edge Delivery Services*, it represents the next generation of performant and scalable storefronts. It's intended to be coupled with Adobe Commerce PaaS or SaaS. 

**Edge Delivery Services** or **EDS** is the next-generation hosting and content delivery framework for *Adobe Experience Manager* or *AEM*. It provides the foundation for **Adobe Commerce Storefront** and is designed to resemble a more *statically generated Jamstack* approach. 

**EDS/AEM Boilerplate** is a specific repo that has a forkable boilerplate for AEM EDS sites as a base. Sites built with this should be forked from this [AEM Boilerplate repo](https://github.com/adobe/aem-boilerplate)

**EDS/AEM Commerce Boilerplate** A specific fork of tthe EDS with the Commerce Drop-ins and the like. Sites built with this should be forked from this [AEM Commerce Boilerplate repo](https://github.com/hlxsites/aem-boilerplate-commerce), it's likely the right starting point for your SaaS project.

**EDS Commerce Drop-in Components** A specific set of drop-ins for Adobe Commerce Storefornt, here's the general selection [here](https://experienceleague.adobe.com/developer/commerce/storefront/dropins/all/introduction/)

**Document-based Authoring** is a way that EDS can 

**Universal Editor** is an in-context content editor that allows Edge Delivery Services to have a nice drag-and-drop content authoring experience, just like *AEM Classic*.

**Adobe Experience Manager** or **AEM** is an enterprise-grade content management system that is often paired with Adobe Commerce. It's a platform that's been around for decades, and *Edge Delivery Services* is the next generation of this platform. Adobe is in the process of re-branding any *EDS* capability as *AEM*.

**AEM Classic** is a pejorative referring to traditional forms of AEM, "anything that has a jar file". This includes *AEM as a Cloud Service*, which is a PaaS service to host AEM. Most self-hosted customers use AEM 6.5. AEM is crazy powerful, and most customers at our scale need it's capabilitites, but it's our understanding that the Classic flavors will be depcreated eventually for *EDS*, *Universal Editor* and adjacent technologies.  

**Magento Open Source** is a community-driven platform supported by Adobe, is is the *PHP Application* that is the foundation for *Adobe Commerce* and shares most of it's capabilitites. It is not compatibile with *App Builder* and requires *In Process Extensibility*.


**Commerce App** refers to any App Builder "app" that is designed for Adobe Commerce, be it by plugging into one of the Out of Process capabilities like Payments, Shipping or Taxes, or by developing something like a Storefront Block which leverages app builder.

**Admin Apps** is a term I will use throughout this guide. It refers to a class of App Builder app that uses the **Admin UI SDK extension points** to present infomration in the Adobe Commerce admin. This is one of the primary use-cases for App Builder.

**Out-of-Process Extensibility** or **OOPE** is the recommended approach for extending Adobe Commerce in a scalable, secure, and maintainable way. Instead of modifying the core PHP application directly, developers use **Adobe Developer App Builder** and external services to integrate new capabilities (such as Payments, Shipping, Taxes, or Storefront Blocks). This keeps the Adobe Commerce core immutable, reduces upgrade friction, and promotes modern cloud-native practices. OOPE is intended to be the long-term strategy for Adobe Commerce development, and is required for *SaaS* development. 

**In-Process Extensibility** or **IPE** is the traditional method of extending Adobe Commerce PaaS or Magento Open Source by directly modifying or adding to the core PHP application. This often includes custom modules, plugins, and observers that run within the same process as the platform itself. While still widely used, IPE can introduce upgrade complexity, security risks, and maintenance challenges. Adobe’s long-term strategy is to reduce reliance on IPE in favor of **Out-of-Process Extensibility (OOPE)**, but it remains necessary for Magento Open Source and some legacy use cases.
