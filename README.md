UIStoryboardSegue-TrueDestination
=================================

Convenience category for UIStoryboardSegue to give you the desired view controller--even when wrapped in a UINavigationController.  Also, return type is `id`, instead of `UIViewController` saving you from having to make an explicit cast.

To use:

 1. Import into a UIViewController subclass
 2.  In prepareForSegue:
<pre><code>
- (void)prepareForSegue:(UIStoryboardSegue *)segue {
    if ([segue.identifier isEqualToString:@"someID"]) {
        SomeCustomViewController *customController = [segue trueDestinationController];
        //	Go about your business
    }
}
</code></pre>