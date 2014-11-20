# Telerik Push Notifications Plugin for Android, iOS, WP8 and Windows 8

## DESCRIPTION

The Telerik Push Notifications is based on the Phonegap Push Plugin: [https://github.com/phonegap-build/PushPlugin](https://github.com/phonegap-build/PushPlugin) and contains some bug fixes, new features and is easily integrated with the Telerik Backend Services.

## Using with Telerik Backend Services

In order to use the plugin with the Telerik Backend Services, which supports iOS, Android, WP8 and Windows 8, take a look at the official documentation:

- [Getting started with Push Notifications in a Hybrid Application with Telerik Backend Services](http://docs.telerik.com/platform/backend-services/getting-started/push-notifications/integrating-push-hybrid)

Or take a look at our hybrid push notifications sample here:

- [Backend Services Push Hybrid simple application](https://github.com/telerik/backend-services-push-hybrid)

- [Backend Services Push Hybrid advanced application](https://github.com/telerik/backend-services-push-hybrid-advanced)

## Features

- Register a device for push notification

         var deviceSpecificOptions = { ... }; // set the device specific options here
		 pushNotification.register(
    			successHandler,
    			errorHandler,
    			deviceSpecificOptions);

- Unregister a device for push notification

		pushNotification.unregister(successHandler, errorHandler, options);

		
- iOS 8 interactive Push Support (coming soon)

		// 1. Configure Notification Action objects - these will be translated to native iOS 8 notification actions
		var readAction = pushNotification.createUserNotificationAction({ 
    		identifier: 'READ_IDENTIFIER', 
    		title: 'Read', 
    		activationMode: PushNotification.ActivationMode.Foreground, // || Background 
    		destructive: false, 
    		authenticationRequired: true 
		}); 
 
		// 2. Create a category object with the actions inside
		var readCategory = pushNotification.createUserNotificationCategory({ 
    		identifier: 'READ_CATEGORY', 
    		actionsForDefaultContext: [readAction], // alert dialog 
    		actionsForMinimalContext: [readAction] // all other notifications 
		}) 
 
		// 3. Register user specified category in the Device. Fires the onUserNotificationSettingsReady callback when done 
		pushNotification.registerUserNotificationSettings({ 
    		types: [PushNotification.NotificationType.Alert, PushNotification.NotificationType.Badge], 
    		categories: [readCategory]
		}, onUserNotificationSettingsReady); 
            

- Set an application icon badge number

		// sets the application badge to the provided value 
		// if badge === 0 clears out the badge 
		pushNotification.setApplicationIconBadgeNumber(badge, callback);
 

- Check if the Push Notifications are enabled on the device

		// Checks whether the Push Notifications are enabled for this Application on the Device 
		pushNotification.areNotificationsEnabled(function(areEnabled) {
		});


- Send Single or Multiple notifications to Android devices

		Single notifications: Send notifications with the same "notId" in the payload of the notification.
		Multiple notifications: Send notifications with different "notId" values in the payload of the notifications. The plugin will then stack these multiple notifications

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