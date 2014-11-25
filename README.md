# Telerik Push Notifications Plugin for Android, iOS, WP8 and Windows 8

## Description

The Telerik Push Notifications is based on the Phonegap Push Plugin: [https://github.com/phonegap-build/PushPlugin](https://github.com/phonegap-build/PushPlugin) and contains some bug fixes, new features and is easily integrated with [Telerik Backend Services](http://www.telerik.com/backend-services).

## Using with Telerik Backend Services

In order to use the plugin with the Telerik Backend Services, which supports iOS, Android, WP8 and Windows 8, take a look at the official documentation:

- [Getting started with Push Notifications in a Hybrid Application with Telerik Backend Services](http://docs.telerik.com/platform/backend-services/getting-started/push-notifications/integrating-push-hybrid)

Or take a look at our hybrid push notifications samples:

- [Backend Services Push Hybrid simple application](https://github.com/telerik/backend-services-push-hybrid)

- [Backend Services Push Hybrid advanced application](https://github.com/telerik/backend-services-push-hybrid-advanced)

## Features

- Register a device for push notification

         var deviceSpecificOptions = { ... }; // set the device specific options here
		 pushNotification.register(successHandler, errorHandler, deviceSpecificOptions);

- Unregister a device for push notification

		pushNotification.unregister(successHandler, errorHandler, options);

		
- iOS 8 interactive Push Support (coming soon)
  
        // Get the push plugin instance
		var pushPlugin = window.plugins.pushNotification;

        // Define a new Read Action
      	var readAction = {
        	identifier: 'READ_IDENTIFIER', // mandatory
        	title: 'Read', // mandatory
        	activationMode: pushPlugin.UserNotificationActivationMode.Foreground, // default: Background
        	destructive: false, // default: false
        	authenticationRequired: true // default: false
      	};

      	// Define a new Ignore Action. Defaults are commented out
      	var ignoreAction = {
	        identifier: 'IGNORE_IDENTIFIER',
        	title: 'Ignore'
        	//activationMode: pushPlugin.UserNotificationActivationMode.Background,
        	//destructive: false,
        	//authenticationRequired: false
      	};

      	// Define a new Delete Action. Defaults are commented out.
      	var deleteAction = {
	        identifier: 'DELETE_IDENTIFIER',
        	title: 'Delete',
        	//activationMode: pushPlugin.UserNotificationActivationMode.Background,
        	destructive: true,
        	authenticationRequired: true
      	};

        // Define a read category with default and minimal context actions
      	var readCategory = {
        	identifier: 'READ_CATEGORY', // mandatory
        	actionsForDefaultContext: [readAction, ignoreAction, deleteAction], // mandatory
        	actionsForMinimalContext: [readAction, deleteAction]  // mandatory
      	};
 
        // Define another category, with different set of actions
      	var otherCategory = {
	        identifier: 'OTHER_CATEGORY', // mandatory
        	actionsForDefaultContext: [ignoreAction, deleteAction], // mandatory
        	actionsForMinimalContext: [deleteAction]  // mandatory
      	};
 
        // Register the category and the other interactive settings.
      	pushPlugin.registerUserNotificationSettings(
          	// the success callback which will immediately return (APNs is not contacted for this)
          	onUserNotificationSettingsReady,
          	// called in case the configuration is incorrect
          	errorHandler,
          	{
            		// asking permission for these features
            		types: [
              			pushPlugin.UserNotificationTypes.Alert,
        	      		pushPlugin.UserNotificationTypes.Badge,
	              		pushPlugin.UserNotificationTypes.Sound
            		],
            		// register these categories
            		categories: [
              			readCategory,
              			otherCategory
            		]
          	}
      	);
            

- Set an application icon badge number

		// sets the application badge to the provided value 
		// if badge === 0 clears out the badge 
		pushNotification.setApplicationIconBadgeNumber(successCallback, errorCallback, badge)
 

- Check if the Push Notifications are enabled on the device

		// Checks whether Push Notifications are enabled for this Application on the Device 
		pushNotification.areNotificationsEnabled(successCallback, errorCallback, options);

##<a name="license"></a> LICENSE

	The MIT License

	Copyright (c) 2012 Adobe Systems, inc.
	portions Copyright (c) 2012 Olivier Louvignes

	Permission is hereby granted, free of charge, to any person obtaining a copy
	of this software and associated documentation files (the "Software"), to deal
	in the Software without restriction, including without limitation the rights
	to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
	copies of the Software, and to permit persons to whom the Software is
	furnished to do so, subject to the following conditions:

	The above copyright notice and this permission notice shall be included in
	all copies or substantial portions of the Software.

	THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
	IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
	FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
	AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
	LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
	OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
	THE SOFTWARE.
