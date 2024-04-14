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
<img src="https://imgur.com/sPkeura.png" height="60%" width="60%" alt="Microsoft Entra Group"/>
</p>
<p>
Please ensure that you set on your Okta account, as this account can be used for a 30-day free trial. To create a user inside Okta, select Directory > People > Add Person > Add User Info and Save. 2.	The new user will appear under the People tab. Select the user that was created > Select Admin roles > Add individual admin privileges > Select the dropdown from the role and select Super Administrator > save changes. This user will have administrator privileges of the Okta account.
</p>
<br />
<h2>Setting up the Identity Provider in Okta</h2>
<p>
<img src="https://imgur.com/mvxha1M.png" height="60%" width="60% alt="IdP"/>
<img src="https://imgur.com/2zr1NfX.png" height="60%" width="60% alt="IdP"/>
<img src="https://imgur.com/2h0v1Jy.png" height="60%" width="60% alt="IdP"/>
</p>
<p>
Next, you will set up the identity provider inside of Okta. Select Security > Identity Providers > Add Identity Provider > Choose SAML as the Identity Provider (IDP) > Select Next > Fill at the required fields under General, Authentication Settings, and Account Matching with IDP username. 4. For SAML Protocol Settings, navigate to your Azure portal > Sign in with your super administrator account (Ensure that P2 licenses is active) > Select Microsoft Entra ID > Select Enterprise applications > New Application > Create New application and name it > Select ‘Integrate any other application you don’t find in the gallery’ > Select create
</p>
<br />
<h2>Setting up the IdP in Azure</h2>
<p>
<img src=".png" height="80%" width="80%" alt="AD Federation"/>
</p>
<p>
.
</p>
<br />
<h2>Setting up the IdP in Azure Continued</h2>
<p>
<img src=".png" height="60%" width="60%" alt="AD Federation"/>
<img src=".png" height="60%" width="60%" alt="AD Federation"/>
</p>
<p>
.
</p>
<br />
<h2>Setting up the IdP in Azure Continued</h2>
<p>
<img src=".png" height="60%" width="60%" alt="Azure"/>
</p>
<p>
.
</p>
<br />
<h2>Linking and Mapping in Okta</h2>
<p>
<img src=".png" height="50%" width="50%" alt="Okta"/>
<img src=".png" height="60%" width="60%" alt="Okta"/>
<img src=".png" height="50%" width="50%" alt="Okta"/>
</p>
<p>
.
</p>
<br />
<h2>Testing out Okta</h2>
<p>
<img src=".png" height="80%" width="80%" alt="Okta"/>
<img src=".png" height="80%" width="80%" alt="Okta"/>
</p>
<p>
.
</p>
<br />
