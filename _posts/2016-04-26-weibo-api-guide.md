---
layout: article
permalink: /posts/2016-04-26-weibo-api-guide
title: "Weibo API Guide"
excerpt: "A guide for programmers and researchers who intend to use Weibo's API. I am writing this guide to support the Social Feed Manager project."
author: victor_tan
tags: [weibo, API, guide, sfm]
---
	
This is a guide for programmers and researchers who intend to use Weibo's API. Since the current [official documentation](http://open.weibo.com/wiki/%E9%A6%96%E9%A1%B5) hasn't been updated for a long time, I am writing this guide to support using [Social Feed Manager](http://go.gwu.edu/sfm) with Weibo's API. 

I highly recommend you ask someone with a Chinese language background if you feel stuck when following this guide. Please make sure you can access to Weibo websites without any problems. Otherwise,it will be hard to complete all the sections.


## 1. Sign Up for a Weibo Account
The goal of this section is to get a `username` and `password` for a weibo account.If you already have one, please go to the next [section](#set-up-a-web-application).

### 1.1 Access to [weibo.com](http://www.weibo.com/)
In the United States, [weibo.com](http://www.weibo.com/) will be redirected to us.weibo.com. The page is as follows:

![weibo index](/images/weibo/weibo_index.png)

### 1.2 Sign Up
Click the `开通微博(Open an Account)` button on the top-right menu. The page may look like this:

![weibo signup](/images/weibo/weibo_signup.png)

It has two ways to fill in the form: `Use Email` and `Use Mobile Phone`, but both of them need your phone number to verify the information. This guide will follow the `Use Mobile Phone` path. The page is shown below:

![weibo signup mobile](/images/weibo/weibo_signup_mobile.png)

Choose the area code for your phone number and after completing all the fields, click the orange button to go to the next step.

### 1.3 Update Information
In this step, you need to provide your basic information. For the gender,`男` (on the left) means male and `女` (on the right) means female.

![weibo update info](/images/weibo/weibo_update_info.png)

Click the orange button to continue.

### 1.4 Select Interests
Choose at least one of the interests on the page and click the orange button to enter Weibo World.

![weibo interests](/images/weibo/weibo_interests.png)

### 1.5 Weibo World
If all the steps above go well, you are now in the Weibo World.

![weibo interests](/images/weibo/weibo_world.png)

If you want to log in next time, just go to [weibo.com](http://www.weibo.com/), click the `登录微博(Sign in)` button and sign in with your phone number and password.

## 2. Set up a Web Application
The goal of this section is to obtain the following three items:

* App Key
* App Secret
* Redirect URI

If you already have all of them, please go to the next [section](#get-access-token).

### 2.1 Go to [http://open.weibo.com](http://open.weibo.com/)
Assuming you have no problem with your firewall blocking weibo.com, please go to [http://open.weibo.com](http://open.weibo.com/) and you will see the following page:

![weibo app](/images/weibo/weibo_app.png)

Click the `登录(Login)` button on the top-right and sign in with your phone number (adding `001` before your number if it does not work at first) and password.

### 2.2 Fill in Basic Information
If successful, click the avatar on the top-right of the screen, and then click the `编辑开发者信息(Update Information)` which is the first option in the menu that pops up.

![weibo basic info](/images/weibo/weibo_basic_info.png)

Next, you will go to the basic information pages, which may look like this:

![weibo fill basic](/images/weibo/weibo_fill_basic.png)

You can use your browser's translation tool (such as what Chrome has) to translate all the fields to your preferred language.

Some of the fields in English:

* 开发这类型: Type of account. '个人' means personal, '公司' means company
* 开发者名称: Developer's name
* 所在地区: Your location. If you are not in China, just choose 海外(Overseas) and 美国(U.S.)
* 紧急联系人姓名: Emergency contact name
* 紧急联系人电话: Emergency contact phone

For the *Emergency contact name* and *Emergency contact phone*, you can simply fill in your own phone number. After completing all of the fields correctly, there will be a green mark on the right. Click the `确认(OK)` button and you should see a confirmation message with a request to send confirmation email. Click the `确认(OK)` button again.

![weibo confirm email](/images/weibo/weibo_confirm_email.png)

On the next page, it will show whether the confirmation email has been sent successfully. After five seconds, you will be redirected to the home page. Now, you need to sign in your email account to confirm the information.

### 2.3 Confirm Your Account
Log in your email account and look for an email from weibo_app@vip.sina.com. The email may look like this:

![weibo confirm link](/images/weibo/weibo_confirm_link.png)

If you don't receive the confirmation email, you need to check the spam. If it still doesn't work, please try again with another email address.

### 2.4 Create a Web Application
If all of the above go smoothly, please go to [open.weibo.com](http://open.weibo.com) and click the `微连接(Microjoining)` link on the menu bar.

![weibo menu app](/images/weibo/weibo_menu_app.png)

Next, you should see a page with types of applications. What most people should choose is `网页应用(Web Application)`.

![weibo app type](/images/weibo/weibo_app_type.png)

You will need to provide an `应用名称(Application Name)`, which must be unique, on the next page. When you are done, click the `创建(Create)` button.

![weibo app create](/images/weibo/weibo_app_create.png)

If successful, you will be redirected to the application manager page. Now, the `App Key` and `App Secret` will display on this page. To set a `Redirect URI`, just click the `高级信息(Advanced Information)` in the sub-menu.

![weibo app done](/images/weibo/weibo_app_done.png)

Then, locate the bar starting with the words OAuth2.0 `接权设置(OAuth2.0 Authorization Setting)`, and click the button `编辑(Edit)` on the right side of the bar.

![weibo uri set1](/images/weibo/weibo_uri_set_1.png)

Finally, you should fill in the two empty fields with any valid URL address. In most cases, it does not matter what you input. Click the green `提交(Submit)` button when you are done.

![weibo uri set2](/images/weibo/weibo_uri_set_2.png)

If you complete all the sections above, you should have the `App Key`, `App Secret` and `Redirect URI`.

## 3. Get Access Token
We need to get an `Access Token` to use most basic APIs. The Weibo API is a REST web service. For the details of using the API, please refer to the [Weibo API Documentation](http://open.weibo.com/wiki/%E5%BE%AE%E5%8D%9AAPI). For more details about OAuth2, please go to the [OAuth2 Documents](http://open.weibo.com/wiki/OAuth/en). There are two steps for the Access Token process:

### 3.1 Get an Authentication Code
To obtain an authentication code, you need to use the [Authorization Service](http://open.weibo.com/wiki/Oauth2/authorize). Provide the information below and leave the `Response type` as the default value.


<form  action="https://api.weibo.com/oauth2/authorize" method="get" target="_blank">
    <label for="client_id">App Key</label>
    <input type="text" id="client_id"  name="client_id" value="">
    
    <label for="redirect_uri">Redirect URL</label>
    <input type="text" id="redirect_uri" name="redirect_uri" value="">
    
    <label for="restype" >Response type</label>
    <input type="text" id="restype" name="restype" value="code">
    
    <input type="submit" value="Submit">
</form>


With the correct information, the new page should look like this:

![weibo auth btn](/images/weibo/weibo_auth_btn.png)

Click the red `授权(Authorize)` button, and you will be redirected to the URL you have provided. Copy the code in the URL to go to next step.

![weibo auth code](/images/weibo/weibo_auth_code.png)

If you have logged out of the session in the previous steps, it may require you sign in with your weibo account again.

### 3.2 Obtain the Access Token
To complete the final step, you should use the [Access Token Service](http://open.weibo.com/wiki/OAuth2/access_token). The `Authentication Code` comes from previous step. Leave the `Grant Type` as the default value.


<form  action="https://api.weibo.com/oauth2/access_token" method="post" target="_blank">
    <label for="client_id">App Key</label>
    <input type="text" id="client_id"  name="client_id" value="">
    
    <label for="client_secret" >App Secret</label>
    <input type="text" id="client_secret" name="client_secret" value="">

    <label for="redirect_uri">Redirect URL</label>
    <input type="text" id="redirect_uri" name="redirect_uri" value="">

    <label for="grant_type" >Grant Type</label>
    <input type="text" id="grant_type" name="grant_type" value="authorization_code">

    <label for="code">Authentication Code</label>
    <input type="text" id="code"  name="code" value="">

    <input type="submit" value="Submit">
</form>

			  

If all is correct, the service will return a JSON format message in the next page.

{% highlight json %}
{"access_token":"2.00biaj5GctqIhB2da047b0c47yeUcB","remind_in":"157679999","expires_in":1700022427,"uid":"5862294965"}
{% endhighlight %}

The `Access Token` above would be `2.00biaj5GctqIhB2da047b0c47yeUcB`. It can last for a long time, usually for 7 years as the `expires_in` field shows.

Now, you have completed all the necessary steps. For a demo of the API, please see the next section.

If you get any unexpected errors in above two steps, request new `Authentication Code` and try again!

## 4. API Examples
In this section, I'll help you understand the API with an example.

[Public Timeline](http://open.weibo.com/wiki/2/statuses/public_timeline): Returns the latest public Weibos.

Enter the `Access Token` from the previous section, and click the Submit button.


<form  action="https://api.weibo.com/2/statuses/public_timeline.json" method="get" target="_blank">
    <label for="access_token" >Access Token</label>
    <input type="text" id="access_token" name="access_token" value="">
    <input type="submit" value="Submit">
</form>


Congratulations! Now, you are a qualified Weibo API programmer. I hope this guide will be helpful to you in the future! If you have any questions, please feel free to contact me: [Yecheng Tan](http://library.gwu.edu/users/ychtan).

## 5. Reference

* [Practical guide for using Sina Weibo's API](https://www.cs.cmu.edu/~lingwang/weiboguide/)
* [Weibo Documentation](http://open.weibo.com/wiki/%E9%A6%96%E9%A1%B5)
* [Weibo OAuth2.0](http://open.weibo.com/wiki/%E6%8E%88%E6%9D%83%E6%9C%BA%E5%88%B6%E8%AF%B4%E6%98%8E)
* [Weibo API](http://open.weibo.com/wiki/%E5%BE%AE%E5%8D%9AAPI)