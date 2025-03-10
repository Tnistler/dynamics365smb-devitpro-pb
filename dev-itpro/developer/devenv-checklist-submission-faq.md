---
title: "Technical Validation FAQ"
description: Describing the most common questions when submitting your app to AppSource.
author: qutreson
ms.custom: na
ms.date: 01/03/2022
ms.reviewer: solsen
ms.suite: na
ms.topic: conceptual
ms.author: qutreson
---

# Technical Validation FAQ

This topic addresses some of the most frequently asked questions around validation of apps for AppSource submission.

## Questions about the validation process

In the following, you can read about how submissions are handled and learn how to address the most common scenarios.

### Against which releases are my apps validated?

The extensions in your submission are validated for all the releases targeted by your submission.

Based on the app.json file of your extension, the service automatically computes the minimum release targeted by your submission and the extensions are then validated for all releases from this minimum release to the current release in production. For more information, see the example in [Technical Validation Checklist](devenv-checklist-submission.md#against-which-releases-of-business-central-is-your-submission-validated). The 'Target Release' (Current, Next Minor, Next Major) available under 'Supplemental Content' in Partner Center is ignored and will be removed.

> [!IMPORTANT]  
> The minimum release computed for your submission also defines the availability in Business Central of all the extensions in your submission.
>
> For example, if the minimum release computed is 18.1, your extensions will be available starting from release 18.1.

> [!NOTE]  
> 30 days before the release of a new [!INCLUDE[prod_short](../includes/prod_short.md)] major version, all submissions are validated against the upcoming release. The apps in your submission must then be compatible with the upcoming release. The goal is to ensure that your customers won't be blocked during the upgrade of their environment.

### Against which countries/regions are my apps validated?

The extensions in your submission are validated for all the countries/regions targeted by the submission which are available in Business Central. You can see which countries/regions you have selected in Partner Center under `Availability > Edit Markets`. 

Note that when adding new localizations in Business Central, these countries/regions can be added to Partner Center before they are actually ready in Business Central. If you are targeting a country/region marked as 'Planned' in [Country/regional availability](../compliance/apptest-countries-and-translations.md), depending on when your submission is processed, your apps might not be uploaded to Business Central if the localization isn't yet ready in Business Central. Generally, it is possible to upload apps for 'Planned' localizations a few weeks before they are officially released. When the localization becomes available, if you are experiencing issues installing your apps, you should increase the version in the app.json and submit the packages again in Partner Center. If you are using Azure Application Insights, you can check whether the country/region was validated using this [Troubleshooting Guide (TSG)](https://go.microsoft.com/fwlink/?linkid=2172328).

### Against which baselines are my apps validated?

The service will verify that your extensions do not introduce breaking changes by comparing them to the latest version available in AppSource for each country validated.

You can know which versions of your extensions were used as baseline during the breaking change validation by enabling Azure Application Insights in your extension and running this [Troubleshooting Guide (TSG)](https://go.microsoft.com/fwlink/?linkid=2172328).

> [!IMPORTANT]  
> As soon as your app has been uploaded to the AppSource marketplace, it will be used as a baseline during the technical validation of your next submissions. As a consequence, you won't be allowed to perform breaking changes without obsoleting the AL objects first and you won't be allowed to perform schema breaking changes; breaking changes on tables or table extensions. This applies also if your extension isn't used by customers yet. You should then not submit your app to the AppSource marketplace if you are still developing it and expect to change it in the near future.

### Which apps are validated in my submission?

The main app and the libraries required by the main app are validated and uploaded to [!INCLUDE[prod_short](../includes/prod_short.md)]. If you have included libraries which are not required by the main app, they will be ignored during the validation and will not be uploaded to the service.

For example, let's consider an app A which has an offer in the AppSource marketplace and A depends on a library named B which doesn't have any dependencies. If you create a new submission with A as the main app and include B, C, and D as libraries, then only A and B will be validated. C and D will be ignored because they are not required by the main app A. If B is updated to depend on C and D, then all apps in the submission will now be validated by the service.

> [!NOTE]  
> If some apps in your submission already have been uploaded to [!INCLUDE[prod_short](../includes/prod_short.md)] with the same version for some countries/regions, then the app will not be validated again for these countries/regions.

> [!IMPORTANT]
> If one or more libraries in your submission have their own offer, their listing(s) in the AppSource marketplace won't be updated automatically. In order to keep the listing(s) in sync with the version of the app(s) uploaded to Business Central, you should submit a submission for their related offer(s).

### How long does the 'Automated application validation' take?

During 'Automated application validation', the apps in your submission are validated for each of the country/regions and each of the releases of [!INCLUDE[prod_short](../includes/prod_short.md)] targeted. If you already have a version of these extensions published to AppSource, then it will also run the breaking change validation using the apps currently in AppSource as baseline. Depending on the size of your app, the validation time can vary. Submissions are generally processed within a few minutes and we expect all submissions to be processed under 3 hours. However, if your app contains thousands of AL files, this can take longer. We would then recommend splitting the app in smaller modules as this would also improve the development experience and the maintainability of your code base.

### How many automated tests do we need to run for validation and how high must the test coverage be?  

When setting up your offer in Partner Center, you must still include a test package in 'App Tests Automation', but it isn't used during the validation of the submission.

Test automation is something we expect you to run, to test your app and to make sure that the quality of your app is high. We do not run tests of your apps, nor do we have a set value for a required code coverage. Instead, we rely on you to test your app properly to give your customers a good experience.

### When I submit an app to AppSource; do you always make a manual validation based on the provided 'Key Usage Scenario' document?  

When setting up your offer in Partner Center, you must still include a document in 'Key Usage Scenario', but it isn't used during the validation of the submission.

We do not run a manual validation of the apps anymore. Instead, we rely on you to test that your app provides your customers with a good experience.

### When are my apps ready to be installed in my Business Central environment?

Shortly after the offer publishing process has been completed in Partner Center, your extensions will be available for installation in Business Central.

Business Central currently does not support installing offers at the "Preview creation" step.

### When should I include my library apps as part of my submission?

You are not required to always include the dependencies of your extension as part of your submission.

You are only required to include the dependencies for your extension as part of your submission if you are submitting a newer version for them. If you do not include them in your submission, they will be downloaded automatically if they are available in Business Central for the targeted countries/regions.

If you did not include the dependencies for your app and they are not available, your submission will fail during the "Automated Application Validation" stage. Failing to find the dependencies for an extension results in error messages with the diagnostic codes `AVS0005` or `AVS0101`.

If you receive an error with the diagnostic code `AVS0107` and a message similar to `The extension 'MyApp' by 'MyPublisher' (version '1.2.3.4') has already been uploaded to Business Central for the country/region 'US'` for one of your library apps, it means that you have already published another .app file for this extension to Business Central as part of a previous submission. This can happen if you submit a .app file with different content, or created by a different build (each .app file created has a specific build ID stamped, so building multiple times the same project results in .app files with different build IDs). If this version of the library is already available for all countries targeted by your submission, you can just remove the extension from the submission. If you are making your library available in new countries, you should use the .app file that has already been uploaded to Business Central or increase the version number in the manifest of the extension (the app.json file).

### My app failed at the "Automated application validation" stage, what do I do next?

At this stage, your extensions are validated to assess whether they meet the requirements specified in the [Technical Validation Checklist](devenv-checklist-submission.md).

If this stage failed with an error message similar to `The validation of the submission failed for X out of Y tasks`, you must investigate what has caused the error. If you are using Azure Application Insights, information about the validation results are logged in Azure Application Insights. You can also use this [Troubleshooting Guide (TSG)](https://go.microsoft.com/fwlink/?linkid=2172328) in order to get started.

> [!NOTE]
> A lot of information is provided in the custom dimensions of the signals. The validation errors can generally be found for the signals with eventId `LC0034`. For more information, see [Analyzing AppSource Submission Validation Trace Telemetry](../administration/telemetry-appsource-submission-validation-trace.md).

If this stage failed with an error message similar to `The extension 'MyApp' by 'MyPublisher' (version '1.2.3.4') has already been uploaded to Business Central for the country/region 'US'`, you must update the list of extensions submitted. For more information, see "When should I include my library apps as part of my submission?".

If this stage failed with an error message similar to `The submission must target at least one existing country/region of Business Central`, your submission does not target any countries/regions currently available in Business Central. If your submission targets a country/region marked as 'Planned' in [Country/regional availability](../compliance/apptest-countries-and-translations.md), you must wait for the localization to become available in Business Central and resubmit your offer. Generally, it is possible to upload apps for new localizations, a few weeks before they are made available to customers.

If this stage failed with an error message similar to `The extension 'MyApp' by 'MyPublisher' (version '1.2.3.4') contains inconsistent information about the package id/name/publisher/version`, it means that something went wrong when the package included in your submission was built. In order to mitigate the issue, you must rebuild the package and submit it again.

If this stage failed with the following error message `Automated validation of the submission has failed. Please retry the operation and contact Partner Center support if it fails again. `, you should create a new submission in Partner Center. If your submission fails again, you should create a support case in Partner Center as documented in this article.

> [!NOTE]
> Because the extensions in your submission are validated for each release and country/region targeted by the submissions, the validation results can be really verbose and cannot always be displayed in their full length in Partner Center. The error message will then end with `...(Truncated)`. If that happens for your submission, you should either enable Azure Application Insights in your extension, run the self-validation script, or fix the errors visible and iterate on your submission.

### My app failed at the "Certification" stage, what do I do next?

At this stage, your extensions are validated to assess whether they meet the requirements defined in the [Marketing Validation Checklist](readiness/readiness-checklist-marketing.md).

Review the Marketing requirements and the [Marketing Validation FAQ](readiness/readiness-marketing-validation-faq.md) in order to fix the errors reported.

### My app failed at the "Publish application with the service" stage, what do I do next?

At this stage, your extensions are being published to Business Central.

If this stage failed with the following error message `Automated upload to Business Central of the extensions in the submission has failed. Please retry the operation and contact Partner Center support if it fails again.`, you should create a new submission in Partner Center. If it fails again, you should create a support case in Partner Center as documented in the dedicated section below.

### My app failed at another stage, what do I do next?

If your submission failed at another stage than "Automated application validation", "Certification", or "Publish application with the service", you should create a support case in Partner Center as documented in the dedicated section below.

## Questions about developing and maintaining AppSource apps

This sections contains frequently asked questions regarding developing apps (in Docker or SaaS). Fore information, about maintaining apps after they have reached the AppSource marketplace, see [Update Lifecycle for AppSource Apps FAQ](devenv-update-app-life-cycle-faq.md).

### What does it mean if I have an app in development that needs another dependency loaded, but I can't get the dependency's codeunits to load in my BC docker instance because it says the dependency's range is outside my range?

It means that your license doesn't allow you to publish that application. A recommendation would be to either get a runtime package from the developer of that AppSource app, which will allow you to bypass the licensing check or to try and test it on an online sandbox environment where that AppSource app is already installed. 

## Questions about code-signing validation

This section contains frequently asked questions related to the code-signing requirement from the [Technical Validation Checklist](devenv-checklist-submission.md). For more information about code-signing, see [Signing an APP Package File](devenv-sign-extension.md).

### Can I use a self-signed certificate to sign my apps targeting AppSource?

No, it is not allowed to use a self-signed certificate. The .app package file must be signed using a certificate purchased from a Certification Authority that has its root certificates in Microsoft Windows. You can obtain a certificate from a range of certificate providers, including but not limited to GoDaddy, DigiCert, and Symantec.

### Do I need to use an EV code-signing certificate to pass the technical validation?

No, it is not required to use an EV code-signing certificate. Standard code-signing certificates can be used to satisfy the code-signing requirement.

### Can I re-use the same code-signing certificate to sign multiple apps?

Yes, you can re-use the same code-signing certificate for multiple extensions. Code-signing certificates have a validity period defined over time.

## Questions about names, affixes, and ID ranges

In the following, you can read about how affixes and ID ranges are assigned.

### Do I need to register different affixes for each of my extensions?

No, you do not need to register affixes for each of your extensions.

The object affixes are registered per publisher so if your apps all have the same publisher, they can share the same affixes. The automated validation verifies that you are using the 3 letter affix registered by Microsoft in your extension, but this still allows you to create longer affixes per extension. For example, if you registered ABC as your affix, you can use ABCD as the prefix in Extension 1 and ABCE as the prefix in Extension 2. For more information, see [Prefix and suffix for naming in extensions](../compliance/apptest-prefix-suffix.md).

### Do I need to request a different ID range for each of my extensions?

No, you do not need to request a new ID range for each of your extensions.

The object IDs are registered per partner, not per extension. You can then use a subset of this range for each of your extensions. It is your responsibility to ensure that you are not defining objects with the same IDs in different extensions. If you are doing so, the extensions defining these objects cannot be installed together on the same environment. For more information, see [Get Started Building Apps](readiness/get-started.md#requesting-an-object-range).

### Will there be any changes made to the object names character limitation (30 characters) within the near future? 

We would like longer names as well. Introducing namespaces could be one investment. However, such a changes has down-stream breaking impact (any caller needs to qualify calls) and there are SQL constraints on name lengths for tables, which currently include company name, table name, app ID and needs to be maximum 255. This is on our long term backlog, but haven't any changes planned in the near future.

## Questions about app identity

This section contains questions related to the identity of apps in AppSource. For more information, see the questions in [App Identity](devenv-app-identity.md).

### When is it okay to change the name of my extension?

Starting from [!INCLUDE[prod_short](../includes/prod_short.md)] 2021 release wave 2 (version 19.0), it is possible to change the name of your extensions.

When renaming an extension, you must:

- increment the version number in the manifest of your extension,
- make sure that your submission only targets releases of Business Central starting from 19.0.
- update the name of your offer in Partner Center - if your extension is the one for which the offer is created.

### When is it okay to change the publisher of my extension?

Starting from [!INCLUDE[prod_short](../includes/prod_short.md)] 2021 release wave 2 (version 19.0), it is possible to change the publisher name of your extensions.

When changing the publisher of an extension, you must:

- increment the version number in the manifest of your extension,
- make sure that your submission only targets releases of Business Central starting from 19.0,
- contact d365val@microsoft.com in order to register your affixes to your new publisher name.

### Is it possible to have multiple apps with the same ID in AppSource? 

Each unique codebase have one unique ID. If you have four apps in AppSource, you need to have four unique IDs for these apps. Otherwise you'll get conflicts. 

### What if we already have an app on AppSource but we need to create the same app for another country; can we then have the same app ID for two different apps targeting two different countries? 

If they are different apps (different code) they should have different identity. Identity is used in, for example, app management, dependencies, support cases, and telemetry. If reused across different apps, identity uniqueness is lost. Another approach could be a common shared (internal/library) app across countries (with one app identity) and localized functionality as extensions on top (with their own identity). 

## Channels to ask questions or report issues

In the following, you can read about how you reach out for support most efficiently.

### When do I contact d365val@microsoft.com?

When registering affixes for your publisher, or adding a new publisher name to your affixes. For more information, see [Benefits and Guidelines for using a Prefix or Suffix](../compliance/apptest-prefix-suffix.md).

### When do I contact Partner Center customer support?

When your submission fails to be successfully completed in Partner Center, but are having issues updating your extension(s) to fix the validation errors.

> [!IMPORTANT]  
> If you are using Azure Application Insights, before opening a support case for a failure at the 'Automated application validation', you must analyze the [signals](../administration/telemetry-appsource-submission-validation-trace.md) emitted in your Azure Application Insights storage. You can do so by using the [Troubleshooting Guide (TSG)](https://go.microsoft.com/fwlink/?linkid=2172328). When opening a support case, you must include the Kusto queries you used and the diagnostic messages you found. Including the results from the TSG is also recommended.

### When do I contact Business Central customer support?

When your submission has been successfully completed in Partner Center, but your customers are experiencing issues installing or using the app.

### When do I log an issue on NavContainerHelper on GitHub?

When you have questions or bugs regarding the self-validation script. For more information, see [https://github.com/microsoft/navcontainerhelper/issues](https://github.com/microsoft/navcontainerhelper/issues).

### When do I write on Yammer?

When you have questions on developing and maintaining AppSource apps or about the validation process, you can ask a question on Yammer. In this group, you will find announcements from Microsoft together with discussions around various AppSource-related topics.

You can join this AppSource group at [aka.ms/BCYammer](https://aka.ms/bcyammer) (note that you need to be a Microsoft partner to do so). If you have problems connecting, please email dyn365bep@microsoft.com. 

## See also

[Technical Validation Checklist](devenv-checklist-submission.md)
