##  Example of avoiding $watch

### HTML

    <div ng-repeat="item in items">
      <span fast-update="name"></span>
    </div>

### JS

	angular.module('lo.directives')
	.directive('fastUpdate', function($rootScope) {
		return {
			link: function(scope, element, attrs) {
				scope.$on('update:binding', function(e, data) {
					// update only specific binding desired
					if (data.index === scope.$index) {
						element.html(data[attrs.fastUpdate]);
					}
				});
			}
		};
	});