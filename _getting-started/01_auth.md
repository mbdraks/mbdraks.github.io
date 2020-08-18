## FortiAuthenticator Configuration - SSOMA

### Configure LDAP
Go to *Authentication - Remote Auth Servers - LDAP* and configure the Windows AD as a LDAP server

![](/assets/images/01_auth/fac-remote-ldap.png)

### Define a filter
Optionally, define a filter to exclude ranges of IPs that should not be considered for the FSSO under *SSO - IP Filtering Rules*

![](/assets/images/01_auth/fac-fgt-sso-ip-filtering.png)


### Define groups
Go to *SSO - FortiGate Filtering* and create a filtering rule for the FortiGate. You can optionally enable a previously defined IP filtering.
Select the groups that will be sent to FortiGate by clicking *Import* and select the LDAP server.

![](/assets/images/01_auth/fac-fgt-sso-fgt-filtering.png)

### Enable SSO
4- Go to *Fortinet SSO Methods - SSO - General* and enable to listen to the FortiGates. Define a secret key.

![](/assets/images/01_auth/fac-fgt-enable-sso.png)

### Enable SSO Mobility Agent (SSOMA)
Also enable FortiClient SSO Mobility Agent, define the secret key (it will be configured at every FCL too), and select how to get the groups. Not caching groups allows easily identifying newly created groups or group change for a user, but will include queries for each new logon which may affect performance.

![](/assets/images/01_auth/fac-fgt-enable-sso-ssoma.png)

## FortiGate Configuration

### Configure FSSO
Configure FSSO External Connector at *Security Fabric - External Connector*

![](/assets/images/01_auth/fgt-extconnector-fsso.png)

Hit *Apply & Refresh* to see the groups obtained from FAC, then hit *OK*.

### Verify
Go to *Dashboard - Users & Devices* and select *Show all FSSO Logons* to see the FSSO events received from FAC

![](/assets/images/01_auth/fgt-fsso-monitor.png)
