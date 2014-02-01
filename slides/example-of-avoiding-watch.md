##  Example of avoiding $watch

### HTML

    <div fast-update-notifier="items" event="'update:item'">
        <div ng-repeat="item in items">
            <span fast-update="name" event="'update:item'"></span>
        </div>
    </div>

### JS

    angular.module('lo.directives')
    .directive('fastUpdateNotifier', function($parse) {
        return {
            compile: function(tElement, tAttrs) {
                var expr = $parse(tAttrs.fastUpdateNotifier),
                    evt = $parse(tAttrs.event);
                return function(scope, element, attrs) {
                    scope.$watch(function() { return expr(scope); }, notify, true);

                    function notify(val) {
                        scope.$broadcast(evt(scope) || 'update:binding', val);
                    }
                };
            }
        };
    })
    .directive('fastUpdate', function($parse) {
        return {
            compile: function(tElement, tAttrs) {
                var expr = $parse(tAttrs.fastUpdate),
                    evt = $parse(tAttrs.event);
                return function(scope, element, attrs) {
                    scope.$on(evt(scope) || 'update:binding', function(e, data) {
                        // update only specific binding desired
                        element.html(data[$index][expr(scope)]);
                    });
                };
            }
        };
    });