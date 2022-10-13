# Module 7 Lesson 4 Lab 14: MedTech service

## Overview

In this lab, you will get experience working with medical IoT data using the [MedTech service](https://docs.microsoft.com/en-us/azure/healthcare-apis/iot/iot-connector-overview) in Azure Health Data Services.

With the rise of wearables and other connected sensor technologies, IoT devices have exploded in the healthcare marketplace. Currently, there is no single data standard for medical IoT device I/O, and this has resulted in many proprietary data models in use across the medical IoT landscape. To provide a centralized platform for medical IoT data connectivity, Microsoft has taken a vendor-agnostic approach, offering the MedTech service toolkit for converting output from any medical IoT device into FHIR. In this lab, we will be using the MedTech service in Azure Health Data Services to map medical IoT data for ingestion into the FHIR service.

In this lab, you will be deploying MedTech service within your Azure Health Data Services workspace, and you will be configuring the service to receive and transform medical IoT data for persistence in FHIR. The steps in this lab are outlined below.

**Exercise 1** - Deploy and configure [Azure Event Hubs](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-about).  
**Exercise 2** - Deploy a MedTech service instance in your Azure Health Data Services workspace.  
**Exercise 3** - Import data mappings for converting medical IoT device data into FHIR.  
**Exercise 4** - Configure Azure Roles for MedTech Service to securely connect to the FHIR service.  
**Exercise 5** - Install tools for creating custom IoT data mappings for storing IoT data in FHIR.  
**Exercise 6** - Import custom IoT data maps into MedTech service.

Have a look at [this document](https://docs.microsoft.com/en-us/azure/healthcare-apis/iot/get-started-with-iot) for an overview of the MedTech service deployment and configuration process (you already deployed an Azure Health Data Services workspace and FHIR service in Lab 7).

## Learning objectives

In this lab, you will:
-   Deploy and configure the MedTech service via Azure portal
-   Deploy and configure additional Azure services required for the MedTech
    service
-   Connect the MedTech service to FHIR service
-   Import a data mapping file for transforming incoming device data into FHIR
-   Inspect medical IoT data flow

## Exercise 1: Deploy and configure Azure Event Hubs

In the first part of this lab, you will use the Azure Portal to deploy an Event Hubs namespace in preparation to create your own Event Hub.

1. [] To begin, navigate to the **Create an Event Hubs namespace** article at +++https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-create#create-an-event-hubs-namespace+++ and follow the instructions for creating an Event Hubs namespace.

1. [] Continue to the next section, **Create an Event Hub** to create your own Event Hub.

===

## Exercise 2: Deploy MedTech service in your Azure Health Data Services workspace

Now you will use Azure Portal to deploy and configure MedTech service within your Azure Health Data Services workspace.

1. [] Open +++https://docs.microsoft.com/en-us/azure/healthcare-apis/iot/deploy-iot-connector-in-azure#deploy-the-medtech-service-manually+++ in a new browser tab to open Deploy MedTech service in the Azure Portal article.

1. [] When you get to the part of the instructions to **Configure MedTech service to ingest data**, for this training it is recommended to use the default **Consumer group** that was assigned when you deployed your Event Hub in the previous exercise (for more information on consumer groups, select the following link, [**Consumer groups**](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-features#consumer-groups "Consumer groups") .

===

## Exercise 3: Import data mappings for converting medical IoT device data into FHIR

In the **Configure Device mapping properties** section, you will be going to [another GitHub repository](https://github.com/microsoft/iomt-fhir/blob/main/docs/Configuration.md#device-content-mapping) and copying two sample data mapping templates to paste directly into MedTech service in Azure portal. You will paste one of the templates in the MedTech service **Device Mapping** tab and another in the MedTech service **Destination** tab. 

1. [] Follow the instructions in the [Deploy the MedTech service using the Azure portal](https://docs.microsoft.com/en-us/azure/healthcare-apis/iot/deploy-iot-connector-in-azure#configure-device-mapping-properties) article under the section, **Configure the device mapping properties**.

1. [] Next, read the  **Device Content Mapping** section in the GitHub repository [here](https://github.com/microsoft/iomt-fhir/blob/main/docs/Configuration.md#device-content-mapping).

1. [] Then go [here](https://github.com/microsoft/azure-health-data-services-workshop/tree/main/Challenge-09%20-%20MedTech%20service/SampleData/Answers) to copy the two sample templates.

> [!NOTE] **Note:** The instructions in the GitHub repository linked above are written for the IoMT FHIR Connector for Azure (OSS), but the same principles apply to MedTech service.

===

## Exercise 4: Configure Azure roles for MedTech service access

Now you will configure permissions so that MedTech service can securely connect with FHIR service and the Event Hub that you deployed in Exercise 1 of this lab. 

1. [] In the **Deploy the MedTech service using the Azure portal** article, continue with the instructions under the **Granting the MedTech service access to the device message event hub and FHIR service** section through to the end of the page.

1. [] Then return here when finished.

> [!NOTE] **Note:** When creating a new mapping, you must click the 'Confirm' button. Pressing ENTER after typing will not work.

===

## Exercise 5: BONUS

Use this [IoT mapper tool](https://github.com/microsoft/iomt-fhir/tree/main/tools/data-mapper) to create maps for the sample messages in the SampleData folder for this lab (accessible at the top of the page). You will find that the SampleData folder has two files. Both files are the same data, but the Three-Sample-Message-Types-with-labels.json has messages with data descriptions and/or units of measure. There are three sample messages in each file - VITALS, BP, and WEIGHT. The VITALS message is an array of data. BP and WEIGHT are single-entry messages.

When you begin the FHIR mapping, you can make up values for the 'Code'. For example - Code: A1235, System: https://loinc.org, Text: Heart Rate.

===

## Exercise 6: BONUS

Import your newly created sample mappings into the MedTech service via the Azure Portal. You can follow the same process in Exercise 3 of this lab to import your custom mappings into MedTech service.

What does success look like for Lab-09?

-   Configure MedTech service for mapping medical IoT device data to FHIR.
-   Generate a custom mapping for medical IoT device data into FHIR.
