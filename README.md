UIStoryboardSegue+TrueDestination.h
====================================

UIStoryboardSegue+TrueDestination.h is a convenience category for UIStoryboardSegue to give you the desired view controller from the `destinationViewController`.  Without this method, the developer is required to do some boilerplate type checking in cases when the desired view controller is wrapped in a `UINavigationController`.

For example, typically you'd have to write something like this in `prepareForSegue:`:

    if ([segue.identifier isEqualToString:@"ItemDetail"]) {
        RBGameItemViewController* viewController = nil;

        if ([[segue destinationViewController] isKindOfClass:[UINavigationController class]]) {
            UINavigationController* navController = [segue destinationViewController];
            viewController = (RBGameItemViewController*)[navController topViewController];
        } else {
            viewController = (RBGameItemViewController*)segue.destinationViewController;
        }
        
        // do something with the view controller
    }
    
Instead, you can write something like this:

    if ([segue.identifier isEqualToString:@"ItemDetail"]) {
        RBGameItemViewController* viewController = [segue trueDestinationController];
        
        // do something with the view controller
    }

Another freebee: the return type is `id` instead of `UIViewController`, saving you from having to make an explicit cast (hey, don't make me type!).

To use:

 1. Import into a `UIViewController` subclass
 2.  In `prepareForSegue:`

    - (void)prepareForSegue:(UIStoryboardSegue *)segue {
        if ([segue.identifier isEqualToString:@"someID"]) {
            SomeCustomViewController *customController = [segue trueDestinationController];
            //	Go about your business
        }
    }
