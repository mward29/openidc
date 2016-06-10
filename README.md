# docker-openidc

### Project using Ping Identities mod_auth_openidc in conjunction with Apache to provide openidconnect functionality with Keycloak in Kubernetes

Included are Kubernetes Ingress, Service and Replication Controller example files.

Below are environment variables that must be set in the container for Apache to consume on startup.

${SSLPROXYVERIFY} on|off

    certificate verification of the remote server

${SSLPROXYCHECKPEERCN} on|off

    remote server certificate's CN field is compared against the hostname of the request URL

${SSLPROXYCHECKPEERNAME} on|off

    host name checking for server certificates when mod_ssl is acting as an SSL client

${SSLPROXYCHECKPEEREXPIRE} on|off

    check if the remote server certificate is expired or not

${SSLPROXYMACHINECERT} path to machine cert. This is a combined file of cert and key. Ex. /etc/kubernetes/ssl/combined.pem

    all-in-one file where you keep the certificate chain for all of the client certs in use

${SSLCERT}

    ssl certificate file ex. /path/to/some/ca.pem

${SSLKEY}

    ssl certificate key file ex. /path/to/some/ca-key.pem

${OIDCPROVIDERMETADATAURL} ex. https://my_domain/auth/realms/demo/.well-known/openid-configuration

    Where 'demo' equals the name of your keycloak realm

${OIDCCLIENTID} realm name from keycloak.

<img src="https://github.com/mward29/openidc/blob/master/realmname.png?raw=true" width="300">

${OIDCCLIENTSECRET} secret from realm. (In this case Keycloak realm secret) ex. below

<img src="https://github.com/mward29/openidc/blob/master/realmsecret.png?raw=true" width="300">

${OIDCCRYPTOPASSPHRASE}

    some random secret you create. ex. biteme

${REDIRECTDOMAIN} domain your apache server is on ex. master.kubernetes.com

    same domain as your Apache server

${SERVERNAME}

    IP of the kubernetes api server you are proxying to. This could also be a domain.
