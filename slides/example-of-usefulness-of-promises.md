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
					}
				}
			}
		}
	});
