##  Example of avoiding $watch

### HTML

    <div fast-update-notifier="items">
        <div ng-repeat="item in items">
            <span fast-update="name"></span>
        </div>
    </div>

### JS

    angular.module('lo.directives')
    .directive('fastUpdateNotifier', function($parse) {
        return {
            compile: function(tElement, tAttrs) {
                var expr = $parse(tAttrs.fastUpdateNotifier);
                return function(scope, element, attrs) {
                    scope.$watch(function() { return expr(scope); }, notify, true);

                    function notify(val) {
                        scope.$broadcast('update:binding', val);
                    }
                };
            }
        };
    })
    .directive('fastUpdate', function($parse) {
        return {
            compile: function(tElement, tAttrs) {
                var expr = $parse(tAttrs.fastUpdate);
                return function(scope, element, attrs) {
                    scope.$on('update:binding', function(e, data) {
                        // update only specific binding desired
                        element.html(data[$index][expr(scope)]);
                    });
                };
            }
        };
    });