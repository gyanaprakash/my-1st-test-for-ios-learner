//appdelegate.h

#import <UIKit/UIKit.h>

@interface AppDelegate : UIResponder <UIApplicationDelegate>

@property (strong, nonatomic) UIWindow *window;


@end

_______________________________________________________________________

//appdelegate.m


#import "AppDelegate.h"
#import "ViewController.h"

@interface AppDelegate ()

@end

@implementation AppDelegate


- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions {
    // Override point for customization after application launch.
    self.window=[[UIWindow alloc]initWithFrame:[[UIScreen mainScreen]bounds]];
    [self.window setBackgroundColor:[UIColor greenColor]];
    [self.window makeKeyAndVisible];
    ViewController *firstvc=[[ViewController alloc]initWithNibName:@"ViewController" bundle:nil];
    self.window.rootViewController=firstvc;
    return YES;
}

- (void)applicationWillResignActive:(UIApplication *)application {
    // Sent when the application is about to move from active to inactive state. This can occur for certain types of temporary interruptions (such as an incoming phone call or SMS message) or when the user quits the application and it begins the transition to the background state.
    // Use this method to pause ongoing tasks, disable timers, and throttle down OpenGL ES frame rates. Games should use this method to pause the game.
}

_______________________________________________________________________________________________________________
//ViewController.h

#import <UIKit/UIKit.h>

@interface ViewController : UIViewController

@property (weak, nonatomic) IBOutlet UITextField *textfield;

- (IBAction)buttonclicked:(id)sender;

@end

______________________________________________________________________________________________________________
//ViewController.m

- (IBAction)resignkeyboard:(id)sender
{
    [self.view endEditing:YES];
}

- (void)textFieldDidEndEditing:(UITextField *)textField
{
    NSLog(@" did end editing :");
    [textfield resignFirstResponder];
        
}

- (IBAction)buttonclicked:(id)sender
{
    
    if (textfield.text.length==0)
    {
        NSLog(@"text filed empty");
        UIAlertView *alert=[[UIAlertView alloc]initWithTitle:@"Warning !" message:@"Enter the value" delegate:self cancelButtonTitle:@"OK" otherButtonTitles:nil, nil];
        [alert show];
    }
    else
    {
        CGFloat y=150;
        int i;
        
        for (i=0; i<[textfield.text intValue]; i++)
        {
            UILabel *lable=[[UILabel alloc]initWithFrame:CGRectMake(40, y, 100, 40)];
            
            // increase the y value according to loop
            y=y+50;
            
            // pass the interger value to the string
            [lable setText:[NSString stringWithFormat:@"%d",i+1]];
            [self.view addSubview:lable];
        }
        
    }
}
@end
