A directory service to sign in & access both Microsoft cloud apps and user-developed cloud apps. Active Directory running on Windows Server provides identity & access management service managed by user organisation.

Azure AD is a cloud-based identity & access management service to help maintain Active Directory deployment.
- services:
	- authentication
	- single sign-on (SSO) - remember only 1 username & password to access multiple apps
	- app management
	- device management - registers devices to be managed
- used by:
	- IT admins - control access to apps & resources based on business requirements
	- app devs - provide standards-based approach for adding functionality to their apps like SSO functionality or enabling an app to work with user's existing credentials
	- users - manage their identities & take maintenance actions
	- online service subscribers - applies to Microsoft 365, Office 356, Azure, Dynamics CRM Online
- Connecting on-premise AD with Azure AD:
	- use Azure AD Connect to sync user identities btwn on-premise Active Directory & Azure AD + changes btwn both identity systems

Active Directory doesn't monitor sign-in attempts until connected with AD at no extra cost.

Azure Active Directory Domain Services (Azure AD DS):
- a service that provides domain services (e.g. domain join, group policy, light weight directory access protocol (LDAP), Kerberos /NTLM authentication)
- no need to deploy, manage, patch domain controllers in cloud to benefit from domain services
- can run legacy apps in cloud that can't use modern authentication methods
- How:
	- at creation, define unique namespace as domain name
	- two Windows Server domain controllers deployed into selected [[Azure regions]] AKA *replica set*
- a managed domain is configured to do one-way sync from AD to AD DS


External Identities - people outside the organisation:
- external users can use their own creds to sign in
- access to apps is managed with AD or AD B2C to protect resources
- capabilities:
	- business to busness (B2B) collaboration - represented in directory as guest users
	- B2B direct connect - establish mutual two-way trust with another AD org for seamless collab
		- currently supports Teams shared channels -> external users can access resources thru their home instance of Teams
		- not represented in directory but visible in Teams shared channel and can be monitored in Teams admin centre reports
	- Azure AD business to customer (B2C) - publish SaaS /custom apps to consumers while using AD B2C for identity & access management

Conditional Access - a tool used to allow / deny access to resources based on identity signals:
- signals depend on identity, location & device of user, as well as what app the user is trying to access
- at sign-in, collect signals from user, makes decisions based on signal, then enforce decision by allowing / denying access request OR multifactor authentication response
- when to use:
	- need multifactor authentication to access app depending on requester's role, location or network
	- need access to services only thru approved client apps
	- need users to access app only from managed devices
	- block app from untrusted sources