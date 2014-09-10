Facebook PHP SDK v4 Examples
============================

Here in this repository I am going to upload all the PHP files related to latest Facebook PHP SDK v4 which will be related to the video series on codenmind.com website.

Usage
-----
All you need to do is to download the whole ./src/Facebook from https://github.com/facebook/facebook-php-sdk-v4 and then upload the downloaded <b>Facebook</b> folder to your hosting and then watch the video tutorials on http://codenmind.com/facebook-sdk-v4-php-tutorials/ to learn that how you can get your own Facebook Developer account and make it up and running after making Facebook Developer account and uploading the <b>Facebook</b> folder to your hosting all you need to do add different lines of code as you can see different examples here like getting basic info about user, posting on timeline etc etc just use different examples and make sure you have included all the classes the first in the start of the index.php file as you can see below:

'''php
<?php
session_start();
require_once( 'Facebook/HttpClients/FacebookHttpable.php' );
require_once( 'Facebook/HttpClients/FacebookCurl.php' );
require_once( 'Facebook/HttpClients/FacebookCurlHttpClient.php' );
require_once( 'Facebook/Entities/AccessToken.php' );
require_once( 'Facebook/Entities/SignedRequest.php');
require_once( 'Facebook/FacebookSession.php' );
require_once( 'Facebook/FacebookSignedRequestFromInputHelper.php');
require_once( 'Facebook/FacebookCanvasLoginHelper.php');
require_once( 'Facebook/FacebookRedirectLoginHelper.php' );
require_once( 'Facebook/FacebookRequest.php' );
require_once( 'Facebook/FacebookResponse.php' );
require_once( 'Facebook/FacebookSDKException.php' );
require_once( 'Facebook/FacebookRequestException.php' );
require_once( 'Facebook/FacebookOtherException.php' );
require_once( 'Facebook/FacebookAuthorizationException.php' );
require_once( 'Facebook/GraphObject.php' );
require_once( 'Facebook/GraphUser.php');
require_once( 'Facebook/GraphSessionInfo.php' );

use Facebook\HttpClients\FacebookHttpable;
use Facebook\HttpClients\FacebookCurl;
use Facebook\HttpClients\FacebookCurlHttpClient;
use Facebook\Entities\AccessToken;
use Facebook\Entities\SignedRequest;
use Facebook\FacebookSession;
use Facebook\FacebookSignedRequestFromInputHelper;
use Facebook\FacebookCanvasLoginHelper;
use Facebook\FacebookRedirectLoginHelper;
use Facebook\FacebookRequest;
use Facebook\FacebookResponse;
use Facebook\FacebookSDKException;
use Facebook\FacebookRequestException;
use Facebook\FacebookOtherException;
use Facebook\FacebookAuthorizationException;
use Facebook\GraphObject;
use Facebook\GraphUser;
use Facebook\GraphSessionInfo;

FacebookSession::setDefaultApplication('549128975195965','32ef50fcca0b1c0175ca74ed2175e88f');

$helper = new FacebookCanvasLoginHelper();

try {
	$session = $helper->getSession();
} catch (FacebookRequestException $ex) {
	echo $ex->getMessage();
} catch (\Exception $ex) {
	echo $ex->getMessage();
}

if ($session) {
	try {
		$request = new FacebookRequest($session, 'GET', '/me');
		$response = $request->execute();
		$me = $response->getGraphObject();
		echo $me->getProperty('name');
	} catch(FacebookRequestException $e) {
		echo $e->getMessage();
	}
} else {
	$helper = new FacebookRedirectLoginHelper('https://apps.facebook.com/APP_NAMESPACE/'); // add your Facebook app namespace here
	$auth_url = $helper->getLoginUrl(array('email')); // add new permission here as an index type array
	echo "<script>window.top.location.href='".$auth_url."'</script>";
}
'''

Visit Us
--------
http://codenmind.com