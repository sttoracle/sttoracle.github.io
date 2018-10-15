---
layout: Step by step instructions
title: IDCS Fusion Apps Integration
---

This guide describes the end-to-end process of configuring FA provisioning Application in IDCS. This App has been tested against Fusion Apps R13 environment.

# **Step-by-step guide**

1.  Download IDCS Metadata to a local XML file

    ![](images/2018-10-15/idcsmetadata.png)
    
    
	>**Note:** **Step 2-10** need to be executed to enable federated SSO 
	with Fusion Apps. If executed against a customer environment, 
	these steps need to be carried out by **Oracle Support**.


2.  Login to internal OAM Console (part of SIM) of the FA environment with OAM admin credential

3.  Go to the <font color="blue"><u>Federation</u></font> tab inside OAM Console. Click on <font color="blue"><u>Service Provider Management</u></font> link

	![](images/2018-10-15/oamconsole.png)
	![](images/2018-10-15/oamfed.png)

4.  Click on <font color="blue"><u>Create Identity Provider Partner</u></font> button

5.  Select <font color="blue"><u>Load from provider metadata</u></font> and choose the locally saved IDCS metadata file.

6.  Provide a name of the IdP partner

	![](images/2018-10-15/oamcreatedidp.png)

7.  Ensure User Mapping attribute is set to <font color="blue"><u>mail</u></font>

	![](images/2018-10-15/oamfedmapping.png)

8. 	 Save the configuration

9.   Obtain the <font color="blue"><u>Entity ID</u></font> from the Federation SP metadata for SIM from **Oracle Support**. Typically it is of the form - [https://{Tenant}-idm.{Domain}/fed
]()

10.  Obtain the SP metadata <font color="blue"><u>Signing Certificate</u></font> for SIM from **Oracle Support**. 

	> If you have access to SIM, you can build the certificate from the metadata. The metadata is avialble from - h[ttps://{Tenant}-idm.{Domain}/fed/sp/metadata](). Once you have the metadata, you can create the certificate file manually using the value of **&lt;X509Certificate&gt;** tag inside the metadata.


9.  Go to <font color="blue"><u>IDCS Admin console</u></font> -&gt; <font color="blue"><u>Applications</u></font> tab

10. Click on **Add** button and select **App Catalog**

    ![](images/2018-10-15/appcatalog.png)
     

11. Search for <font color="blue">Oracle Fusion Applications Prov</font> App and **Add**

	![](images/2018-10-15/appadd.png)

12. On the first page of Configuration screen provide the <font color="blue">Tenant Name</font> and <font color="blue">Domain Name</font> values for your Fusion App environment. 

	![](images/2018-10-15/appdetails.png)

13. Click on **Next**

14. Provide the noted <font color="blue">Entity ID</font> value. Upload the <font color="blue">Signing Certificate</font> previously saved.

	![](images/2018-10-15/appsso.png)

14. Click on **Next**
   
15. Switch on the **Enable Provisioning** slider

	![](images/2018-10-15/appprovenable.png)
   
16. Provide *Administrator Username*, *Password*, FA Env *Hostname* for REST API (Format - [&lt;tenant&gt;-hcm.&lt;domain&gt;]()) and *port number* (443). Also select *SSL Enabled* checkbox.

18. Test the connectivity

	![](images/2018-10-15/appprovtest.png)

25. Switch on the **Enable Synchronization** slider

	![](images/2018-10-15/appprovsync.png)

26. Click on **Finish** button

27. **Activate** the application

	![](images/2018-10-15/appactivate.png)
	![](images/2018-10-15/appdone.png)

28. Go to the **Import** tab of the application

29. Click on the **Import** link. It will start the **Import job**.

	![](images/2018-10-15/appjob.png)

30. Refresh the page after a while

31. Verify that the job is completed and existing FA users have been imported and displayed on the page

	![](images/2018-10-15/appjobdone.png)

32. Go to the **Users** tab of the application and click on **Assign**

33. Select a user

	![](images/2018-10-15/appassign.png)

34. Verify that user is successfully assigned to the App

	![](images/2018-10-15/appprovsuccess.png)

36. Go to an Incognito browser window and login to IDCS **MyConsole** using the assigned user’s credentials

	![](images/2018-10-15/apptestlogin.png)

37. Verify that the **Fusion Applications** are displayed there

	![](images/2018-10-15/apptestmyapp.png)

38. Click on the <font color="blue">Oracle Fusion Applications Prov HCM</font> app

39. Verify **SSO**

 