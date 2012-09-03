UIStoryboardSegue-TrueDestination
=================================

Convenience category for UIStoryboardSegue to give you the desired view controller--even when wrapped in a `UINavigationController`.  Without this method, the developer is required to do some boilerplate type checking in cases where the desired view controller is wrapped in a `UINavigationController`.
Another freebee: return type is `id` instead of `UIViewController`, saving you from having to make an explicit cast (hey, don't make me type!).

To use:

 1. Import into a UIViewController subclass
 2.  In prepareForSegue:

    - (void)prepareForSegue:(UIStoryboardSegue *)segue {
        if ([segue.identifier isEqualToString:@"someID"]) {
            SomeCustomViewController *customController = [segue trueDestinationController];
            //	Go about your business
        }
    }
