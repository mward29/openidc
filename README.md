# docker-openidc

### Project using Ping Identities mod_auth_openidc in conjunction with Apache to provide openidconnect functionality with Keycloak in Kubernetes

Included are Kubernetes Ingress, Service and Replication Controller example files.

Below are environment variables that must be set in the container for Apache to consume on startup.

${SSLPROXYVERIFY} on|off

${SSLPROXYCHECKPEERCN} on|off

${SSLPROXYCHECKPEERNAME} on|off

${SSLPROXYCHECKPEEREXPIRE} on|off

${SSLPROXYMACHINECERT} path to machine cert. This is a combined file of cert and key. Ex. /etc/kubernetes/ssl/combined.pem

${SSLCERT} ssl certificate file ex. /path/to/some/ca.pem

${SSLKEY} ssl certificate key file ex. /path/to/some/ca-key.pem

${OIDCPROVIDERMETADATAURL} ex. https://my_domain/auth/realms/demo/.well-known/openid-configuration
  Where 'demo' equals the name of your keycloak realm

${OIDCCLIENTID} realm name from keycloak.

![Alt text](file:///Users/uwardm5/Desktop/Screen%20Shot%202016-06-10%20at%204.58.17%20PM.png "Optional title")

${OIDCCLIENTSECRET} secret from realm. (In this case Keycloak realm secret) ex. dbc1r12f-ef60-364d-b1ed-97c35td1bccf

${OIDCCRYPTOPASSPHRASE} some random secret you create. ex. biteme

${REDIRECTDOMAIN} domain your apache server is on ex. master.kubernetes.com

${SERVERNAME} IP of the kubernetes api server you are proxying to. This could also be a domain.
