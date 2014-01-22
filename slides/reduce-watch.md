##  Reduce $watch

*  scope.$watch most performance exhausting portion
*  Callbacks with `$watch` run at least once during `$digest`, often twice
