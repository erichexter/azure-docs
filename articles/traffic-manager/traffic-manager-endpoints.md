---
title: Manage endpoints in Azure Traffic Manager | Microsoft Docs
description: This article will help you add, remove, enable and disable endpoints from Azure Traffic Manager.
services: traffic-manager
documentationcenter: ''
author: kumudd
manager: timlt
editor: tysonn

ms.assetid: 038270d1-28ba-4078-9c5d-37fc5d683be6
ms.service: traffic-manager
ms.devlang: na
ms.topic: get-started-article
ms.tgt_pltfrm: na
ms.workload: infrastructure-services
ms.date: 03/17/2016
ms.author: kumud
---

# Add, disable, enable or delete endpoints

The Web Apps feature in Azure App Service already provides failover and round-robin traffic routing functionality for websites within a datacenter, regardless of the website mode. Azure Traffic Manager allows you to specify failover and round-robin traffic routing for websites and cloud services in different datacenters. The first step necessary to provide that functionality is to add the cloud service or website endpoint to Traffic Manager.

> [!NOTE]
> You cannot add external locations or Traffic Manager profiles as endpoints using the Azure classic portal. You must use the REST API [Create Definition](http://go.microsoft.com/fwlink/p/?LinkId=400772) or Windows PowerShell [Add-AzureTrafficManagerEndpoint](http://go.microsoft.com/fwlink/p/?LinkId=400774).

You can also disable individual endpoints that are part of a Traffic Manager profile. Endpoints include both cloud services and websites. Disabling an endpoint leaves it as part of the profile, but the profile acts as if the endpoint is not included in it. This action is very useful for temporarily removing an endpoint that is in maintenance mode or being redeployed. Once the endpoint is up and running again, it can be enabled.

> [!NOTE]
> Disabling an endpoint has nothing to do with its deployment state in Azure. A healthy endpoint will remain up and able to receive traffic even when disabled in Traffic Manager. Additionally, disabling an endpoint in one profile does not affect its status in another profile.

## To add a cloud service or website endpoint

1. On the Traffic Manager pane in the Azure classic portal, locate the Traffic Manager profile that contains the endpoint settings that you want to modify, and then click the arrow to the right of the profile name. This will open the settings page for the profile.
2. At the top of the page, click **Endpoints** to view the endpoints that are already part of your configuration.
3. At the bottom of the page, click **Add** to access the **Add Service Endpoints** page. By default, the page lists the cloud services under **Service Endpoints**.
4. For cloud services, select the cloud services in the list to enable them as endpoints for this profile. Clearing the cloud service name removes it from the list of endpoints.
5. For websites, click the **Service Type** drop-down list, and then select **Web app**.
6. Select the websites in the list to add them as endpoints for this profile. Clearing the website name removes it from the list of endpoints. Note that you can only select a single website per Azure datacenter (also known as a region). If you select a website in a datacenter that hosts multiple websites, when you select the first website, the others in the same datacenter become unavailable for selection. Also note that only Standard websites are listed.
7. After you select the endpoints for this profile, click the checkmark on the lower right to save your changes.

> [!NOTE]
> If you are using the *Failover* traffic routing method, after you add or remove an endpoint, be sure to adjust the Failover Priority List on the Configuration page to reflect the failover order you want for your configuration. For more information, see [Configure Failover traffic routing](traffic-manager-configure-failover-routing-method.md).

## To disable an endpoint

1. On the Traffic Manager pane in the Azure classic portal, locate the Traffic Manager profile that contains the endpoint settings that you want to modify, and then click the arrow to the right of the profile name. This will open the settings page for the profile.
2. At the top of the page, click **Endpoints** to view the endpoints that are included in your configuration.
3. Click the endpoint that you want to disable, and then click **Disable** at the bottom of the page.
4. Traffic will stop flowing to the endpoint based on the DNS Time-to-Live (TTL) configured for the Traffic Manager domain name. You can change the TTL from the Configuration page of the Traffic Manager profile.

## To enable an endpoint

1. On the Traffic Manager pane in the Azure classic portal, locate the Traffic Manager profile that contains the endpoint settings that you want to modify, and then click the arrow to the right of the profile name. This will open the settings page for the profile.
2. At the top of the page, click **Endpoints** to view the endpoints that are included in your configuration.
3. Click the endpoint that you want to enable, and then click **Enable** at the bottom of the page.
4. Traffic will start flowing to the service again as dictated by the profile.

## To delete a cloud service or website endpoint

1. On the Traffic Manager pane in the Azure classic portal, locate the Traffic Manager profile that contains the endpoint settings that you want to modify, and then click the arrow to the right of the profile name. This will open the settings page for the profile.
2. At the top of the page, click **Endpoints** to view the endpoints that are already part of your configuration.
3. On the Endpoints page, click the name of the endpoint that you want to delete from the profile.
4. At the bottom of the page, click **Delete**.

> [!NOTE]
> You cannot delete external locations or Traffic Manager profiles as endpoints using the Azure classic portal. You must use Windows PowerShell. For more information, see [Remove-AzureTrafficManagerEndpoint](https://msdn.microsoft.com/library/dn690251.aspx).

## Next steps

* [Configure failover routing method](traffic-manager-configure-failover-routing-method.md)
* [Configure round robin routing method](traffic-manager-configure-round-robin-routing-method.md)
* [Configure performance routing method](traffic-manager-configure-performance-routing-method.md)
* [Troubleshooting Traffic Manager degraded state](traffic-manager-troubleshooting-degraded.md)
* [Operations on Traffic Manager (REST API Reference)](http://go.microsoft.com/fwlink/p/?LinkID=313584)

