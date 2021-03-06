---
title: "Add API Methods"
description: "In this section, you'll learn how to authenticate users on an iOS app using the WeDeploy Swift API Client."
buttonTitle: "I added the API methods"
tutorialTitle: "Getting started with WeDeploy Auth on an iOS app"
parentId: "auth-ios"
layout: "tutorial"
time: 90
weight: 7
---

#### Add API Methods

###### Create User

First, let's add the code that will allow users to create an account. 

To do this, go to `tutorial-auth-ios/app/tutorial-auth-ios/SignUpViewController.swift` and paste this code in the "signUpButtonClick" function:

```swift
WeDeploy.auth("auth.<your-project-id>.wedeploy.io")
	.createUser(email: emailText, password: passwordText, name: nameText)
	.toCallback { auth, error in
		if let _ = auth {
			self.showAlert(with: "Success", message: "Sign-up successfully")
		}
		else {
			self.showAlert(with: "Error", message: "Sign-up failed.")
		}
	}
```

**Note:** make sure to replace `<your-project-id>` with the id of your project.

Now you can run the app, click on create an account button, fill the fields and create a new user!

###### Sign-in

Next, let's add the code that will allow users to sign-in. 

First of all, go to `tutorial-auth-ios/app/tutorial-auth-ios/LoginViewController.swift`, and paste this code in the "loginButtonClick" function:

```swift
WeDeploy.auth("auth.<your-project-id>.wedeploy.io")
	.signInWith(username: usernameText, password: passwordText)
	.toCallback { auth, error in
		self.handleLoginResult(auth: auth, error: error)
	}
```

If you run the app and fill the login fields you can login into WeDeploy!

<aside>

###### <span class="icon-16-star"></span> Pro Tip

In the examples above we use the toCallback method to handle the response with a callback, which is the most typical way of doing it in the iOS ecosystem, 
but we can also handle the result using a promise:

```swift
WeDeploy.auth("auth.<your-project-id>.wedeploy.io")
	.signInWith(username: usernameText, password: passwordText)
	.then { auth in
		self.handleLoginResult(auth: auth, error: nil)
	}
	.catch { error in
		self.handleLoginResult(auth: nil, error: error)
	}
```

or even a observable!

```swift
WeDeploy.auth("auth.<your-project-id>.wedeploy.io")
	.signInWith(username: usernameText, password: passwordText)
	.toObservable()
	.subscribe(onNext: { auth in
		self.handleLoginResult(auth: auth, error: nil)
	}, onError: { error in
		self.handleLoginResult(auth: nil, error: error)
	})
```
</aside>