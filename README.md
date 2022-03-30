# Custom EOEPCA Jupyterhub
## EOEPCA Authenticator
To integrate jupyterhub with EOEPCA system we created a new authenticator, this authenticator extend the GenericOAuthenticator provided by Jupyterhub oauthenticator package.
Three functions are overwritten/developed to add the functionability we need:
1. The ***_get_user_data*** function: Gluu returns the authentication method in the token call as "***b**earer*" but ask for "***B**earer*" in the userinfo call. This function is overwritten just to capitalize this "*b*"
2. The ***_create_auth_state*** function: This function is overwritten to add the id_token to our saved auth_state, this way we can get it when we spawn the user jupyterlab. More information that we can need can be stored here.
3. The ***pre_spawn_start*** function: This function is developed to pass the id_token to the spawned user jupiterlab, it is passed as an environment variable called ID_TOKEN. More information can be passed this way, maybe possible to pass it in a different way too.



