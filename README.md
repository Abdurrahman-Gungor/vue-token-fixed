# Project Forked 
This project is fork of [Vue-Token](https://github.com/joostlawerman/Vue-Token).

This fork fixed the ***Vue Resource Http*** and ***Vue Router*** error.

# Vue-Token
Simple token storage/ authorization in vuejs.

This plugin requires you to initialize the [vue-resource](https://github.com/vuejs/vue-resource) plugin first.

The token will be stored into the Authorization header with each request you make with the vue-resource plugin.

	npm install vue-token-fixed --save

# Usage

	import Auth from 'vue-token-fixed';	
	import router from './router';
	Vue.use(Auth, options);

## Options

	{
	 	router: router,
		loginUrl: "/api/login", 
		signupUrl: "/api/users", 
		logoutUrl: "/api/logout"
		refresh: false // Utalize the automatic refresh of tokens (it will use the token from response.token as the new token)
	}

## Example Component

	<script>
	export default {
		data(){
			return {
				input: {
					email: "",
					password: ""
				}
			}
		},
		created(){
			//
		},
		methods: {
			send() {
            	this.$auth.login(this, this.input, "Redirect to path after login", (errors) => {
					console.log(errors);
            	});
            }
		}
	}
	</script>

## Methods

	$auth.
		// Send a (post) request to the loginUrl.
		login(input, redirect = false, errorHandler = false)
			
		// Send a (post) request to the signupUrl.
		register(input, redirect = false, errorHandler = false login = true)
			
		//Send a (get) request to the logoutUrl.
		logout(redirect = false, errorHandler = false)
			
		//Check if a token is being stored and if is not null.
		check()
			
		//Get the token from the localStorage.
		getToken()
			
		//Set a token in the localStorage.
		setToken(token)
			
		//Remove the token from the localStorage.
		removeToken()

# License
[MIT](https://github.com/Abdurrahman-Gungor/vue-token-fixed/blob/master/LICENSE)# vue-token-fixed

