##  More optimization facts/tricks

*  Sometimes worthwhile to do `$digest` instead of full `$apply()`
*  Use `track by` syntax for ng-repeat to avoid rapid destruction and recreation of DOM nodes
*  Use `$parse` and link $scope instead of $scope.$eval
*  (Hack) Add a callback to `$scope.$$postDigest`
  *  For updating the DOM after `$digest`
  *  Postpones rendering of DOM until model stabilizes