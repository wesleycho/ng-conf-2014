##  Example of usefulness of promises

### JS

	$stateProvider.state('welcome', {
		url: '/',
		views: {
			main: {
				templateUrl: ...,
				controller: ...,
				resolve: {
					data: function($http) {
						return $http.get('/api/welcome/data')
									.then(resolve, reject);
					},
					role: function(auth) {
						return auth.getRole()
								   .then(checkAuthorization)
								   .then(null, redirect);
					}
				}
			}
		}
	});
