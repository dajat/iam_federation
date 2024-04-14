<p align="center">
<img src="https://imgur.com/Eisrkr6.png" height="40%" width="40% alt=" AD Federation"/>
</p>

<h1>Active Directory Federation using Okta (Azure)</h1>

This tutorial outlines configuring both Okta and Azure by creating an Identity Provider inside of Azure and ensuring that the IdP inside of Okta matches for users to sign in successfully. This project will outline the implementation process and configurations of both applications. Please ensure that the following subscriptions are active. Please review the links below for more information on each subscription:

- [Entra ID Premium P2](https://www.microsoft.com/en-us/security/business/microsoft-entra-pricing)
- [Okta Developer Account](https://www.okta.com/free-trial/)

<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Microsoft Entra ID)
- Okta

<h2>Installation Steps</h2>

<h2>Creating a User inside of Okta</h2>
<p>
<img src="https://imgur.com/byDJ1mI.png" height="60%" width="60%" alt="Microsoft Entra Group"/>
<img src="https://imgur.com/sPkeura.png" height="60%" width="60%" alt="Microsoft Entra Group"/>
</p>
<p>

- To create a user in Okta, select Directory > People > Add Person > Add User Info > Save. The new user will appear under the People tab. Next, you will give the user administrative privileges.
- Select the user that was created > Select Admin roles > Add individual admin privileges > Select the dropdown from the role and select Super Administrator > Save changes.
</p>
<br />
<h2>Setting up the Identity Provider in Okta</h2>
<p>
<img src="https://imgur.com/mvxha1M.png" height="60%" width="60% alt="IdP"/>
<img src="https://imgur.com/2zr1NfX.png" height="60%" width="60% alt="IdP"/>
<img src="https://imgur.com/2h0v1Jy.png" height="60%" width="60% alt="IdP"/>
</p>
<p>

- Next, you will set up the identity provider inside of Okta. Select Security > Identity Providers > Add Identity Provider > Choose SAML as the Identity Provider (IDP) > Select Next > Fill in the required fields under General, Authentication Settings, and Account Matching with IDP username.
- For SAML Protocol Settings, navigate to your Azure portal > Sign in with your super administrator account > Select Microsoft Entra ID > Select Enterprise applications > New Application > Create New application and provide a name for the application > Select ‘Integrate any other application you don’t find in the gallery’ > Select Create
</p>
<br />
<h2>Setting up the IdP in Azure</h2>
<p>
<img src="https://imgur.com/f4pxRkL.png" height="60%" width="60%" alt="AD Federation"/>
<img src="https://imgur.com/Idw7YWy.png" height="80%" width="80%" alt="AD Federation"/>
</p>
<p>

- After creating the application, select ‘Setup Single Sign On (SSO)’ > Select SAML for the SSO method > Fill out the Identifier (Entity ID) and Reply URL by creating a dummy URL (We’ll get back to this part later) > Select Save.
- Next, select Attributes and Claims and fill in the information that will be sent to Okta. Keep in mind that this information is sent from Azure to Okta and it must match for the user to receive access.
- Open a current attribute claim and copy the ‘Namespace schema’, as this is very important for mapping and bringing over information. Add a name for the claim > Paste in the schema URL > Name the source attribute > Select Save
</p>
<br />
<h2>Setting up the IdP in Azure Continued</h2>
<p>
<img src="https://imgur.com/z14W9LP.png" height="60%" width="60%" alt="AD Federation"/>
<img src="https://imgur.com/79f5JQc.png" height="60%" width="60%" alt="AD Federation"/>
<img src="https://imgur.com/1E5fQ97.png" height="60%" width="60%" alt="AD Federation"/>
</p>
<p>

- Next, you will create a new SAML certificate > Select Save > Select the three dots to download the Base 64 Certificate download. Go back to the IDP provider screen in Okta and enter the IDP Issue URI, IDP SSO URL, and the IDP signature Certificate under SAML Protocol Settings > Select Finish.
- Next, you will collect the Audience URI (from Okta) to add to the Identifier (Entity ID) and the Assertion Consumer Service URL (from Okta) to add to the Reply URL inside Azure.
</p>
<br />
<h2>Linking and Mapping in Okta</h2>
<p>
<img src="https://imgur.com/PfNlpGv.png" height="50%" width="50%" alt="Okta"/>
</p>
<p>

- Next, you will begin mapping the attributes inside of Okta that will transferred from Azure.
- Select Edit Profile and mappings inside of the Okta IdP > Mappings to unmap all mappings under the ‘All’ tab and Save > Remove all custom attributes and select Save (Wait 30 seconds).
- Select Add Attribute under Custom and list the following above > Select Save.
</p>
<br />
<h2>Testing out Okta</h2>
<p>
<img src="https://imgur.com/sZBTKZT.png" height="80%" width="80%" alt="Okta"/>
<img src="https://imgur.com/wBcs7hK.png" height="80%" width="80%" alt="Okta"/>
<img src="https://imgur.com/sjva3UT.png" height="80%" width="80%" alt="Okta"/>
</p>
<p>

- Next, test out the linking of Okta and Azure by assigning users to the application.
- Select Users and Groups under the application that was created earlier > Add new user/group > Select Single Sign > Test > Test Sign On.
- Make sure that the attributes that are assigned in Okta are filled out in Azure under the users and groups of the Okta enterprise application.
</p>
<br />
