# Vue-Token
Simple token storage/ authorization in vuejs.

This plugin requires you to initialize the [vue-resource](https://github.com/vuejs/vue-resource) plugin first.

The token will be stored into the Authorization header with each request you make with the vue-resource plugin.

	npm install vue-token-fixed --save
	
# Usage

	import Auth from 'vue-token-fixed';	
	import router from './router';
	Vue.use(Auth, options);
	
# router.js (Sample)

	import Vue from 'vue'
	import VueRouter from 'vue-router'

	Vue.use(VueRouter)

	function load (component) {
 	 return () => import(`@/${component}.vue`)
	}

	const vueRoter = new VueRouter({
 	 mode: 'hash',

 	 routes: [
   	 {
    	{ path: '/login', component: load('Login') },
    	{ path: '*', component: load('Error404') } // Not found
  	]
	})

	export default vueRoter


## Options

	{
	 	router: router,
		loginUrl: "/api/login", 
		signupUrl: "/api/users", 
		logoutUrl: "/api/logout"
		refresh: false // Utalize the automatic refresh of tokens
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
		methods: {
			send() {
            	this.$auth.login({email:this.input.email,password:this.input.password}, "Redirect to path after login", (errors) => {
					console.log(errors);
            	});
            }
		}
	}
	</script>

## Methods

	$auth.
		// Send a (get) request to the loginUrl.
		login(fieldInfos, redirect = false, errorHandler = false)
			
		// Send a (post) request to the signupUrl.
		register(fieldInfos, redirect = false, errorHandler = false login = true)
			
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

# Note
	In Ajax requests, the returned token object is taken as "data.token".

# License
[MIT](https://github.com/Abdurrahman-Gungor/vue-token-fixed/blob/master/LICENSE)# vue-token-fixed

