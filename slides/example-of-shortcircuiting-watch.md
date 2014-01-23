##  Example of shortcircuiting $watch

### JS

	$scope.$watch(function() {
		return $scope.bigList.map(function(bigObject) {
			return bigObject.foo.bar;
		});
	}, function(val) {...}, true);