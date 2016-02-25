Cordova Facebook plugin
====================

# Overview #
facebook login, prompt wall post, publish wall post, publish score, show leaderboard and invite.

[android, ios] [crodova cli] [xdk] [cocoon] [phonegap build service]

Requires facebook developer account https://developers.facebook.com/apps

This is open source cordova plugin.

You can see Cordova Plugins in one page: http://cranberrygame.github.io?referrer=github

```c
```
# Change log #
```c
```
# Install plugin #

## Cordova cli ##
https://cordova.apache.org/docs/en/edge/guide_cli_index.md.html#The%20Command-Line%20Interface - npm install -g cordova@6.0.0
```c
//caution: replace 1388298811491111 with your app id and Avoid Bird with your app name
cordova plugin add cordova-plugin-share-facebook --variable APP_ID="1388298811491111" --variable APP_NAME="Avoid Bird"
```
## Xdk ##
//caution: replace 1388298811491111 with your app id and Avoid Bird with your app name
<img src="https://raw.githubusercontent.com/cranberrygame/cordova-plugin-share-facebook/master/doc/xdk_APP_ID.png"><br>
https://github.com/cranberrygame/cordova-plugin-share-facebook/blob/master/doc/intelxdk.config.additions.xml
```c
```

## Cocoon ##
https://cocoon.io - Create project - [specific project] - Setting - Plugins - Custom - Git Url: https://github.com/cranberrygame/cordova-plugin-share-facebook.git - INSTALL - Save<br>
//caution: replace 1388298811491111 with your app id and Avoid Bird with your app name<br>
//caution: if APP_NAME Name parameter's Avoid Bird Value is not equal to your app name (Avoid Bird), then build error (cocoon (cordova5 build issue)).<br>
https://cocoon.io - Create project - [specific project] - Setting - Plugins - Installed - Git Url https://github.com/cranberrygame/cordova-plugin-share-facebook.git - ADD PARAMETER - Name: APP_ID Value: 1388298811491111 - Name: APP_NAME Value: Avoid Bird - Save<br>
<img src="https://raw.githubusercontent.com/cranberrygame/cordova-plugin-share-facebook/master/doc/cocoon_APP_ID1.png"><br>
<img src="https://raw.githubusercontent.com/cranberrygame/cordova-plugin-share-facebook/master/doc/cocoon_APP_ID2.png">

## Phonegap build service (config.xml) ##
https://build.phonegap.com/ - Apps - [specific project] - Update code - Zip file including config.xml
```c
//caution: replace 1388298811491111 with your app id and Avoid Bird with your app name
<gap:plugin name="cordova-plugin-share-facebook" source="npm" >
    <param name="APP_ID" value="1388298811491111" />
    <param name="APP_NAME" value="Avoid Bird" />
</gap:plugin>
```

## Construct2 ##
Download construct2 plugin: http://www.paywithapost.de/pay?id=4ef3f2be-26e8-4a04-b826-6680db13a8c8
<br>
Now all the native plugins are installed automatically: https://plus.google.com/102658703990850475314/posts/XS5jjEApJYV
<br>
You can also use this plugin's AccessToken with lanceal's various facebook related plugins: https://www.scirra.com/forum/facebook_t111941
# Server setting #

<img src="https://raw.githubusercontent.com/cranberrygame/cordova-plugin-share-facebook/master/doc/APP_ID_1-1.png"><br>
<img src="https://raw.githubusercontent.com/cranberrygame/cordova-plugin-share-facebook/master/doc/APP_ID_1-2.png"><br>
<img src="https://raw.githubusercontent.com/cranberrygame/cordova-plugin-share-facebook/master/doc/APP_ID_1-3.png"><br>
<img src="https://raw.githubusercontent.com/cranberrygame/cordova-plugin-share-facebook/master/doc/APP_ID_1-4.png"><br>
https://raw.githubusercontent.com/cranberrygame/cordova-plugin-share-facebook/master/doc/APP_ID_1-4.txt
<img src="https://raw.githubusercontent.com/cranberrygame/cordova-plugin-share-facebook/master/doc/APP_ID_1-5.png"><br>
https://raw.githubusercontent.com/cranberrygame/cordova-plugin-share-facebook/master/doc/APP_ID_1-5.txt
<img src="https://raw.githubusercontent.com/cranberrygame/cordova-plugin-share-facebook/master/doc/APP_ID_2-1.png"><br>
<img src="https://raw.githubusercontent.com/cranberrygame/cordova-plugin-share-facebook/master/doc/APP_ID_ios1.png"><br>
<img src="https://raw.githubusercontent.com/cranberrygame/cordova-plugin-share-facebook/master/doc/APP_ID_ios2.png"><br>
<img src="https://raw.githubusercontent.com/cranberrygame/cordova-plugin-share-facebook/master/doc/APP_ID_ios3.png">

```c
[android]

https://developers.facebook.com/apps - Add a New App - ... - Skip Quick Start

Put your app id and your app name to Phonegap Facebook plugin's c2 property.

cf)How to get Key Hashes (facebook)

cd /d D:\sign\android
keytool -list -v -keystore mykey.keystore -alias mykeystore

SHA1: 90:2F:37:48:~~~~~~:09:2D:61:52:E6

convert upper SHA1 to base64 string for facebook from following site.
http://tomeko.net/online_tools/hex_to_base64.php?lang=en

==> Key Hashes: kC83~~~~~~~~~1hUuY=
```
# API #
```javascript
preparing api
/*
//
var leaderboardId = "REPLACE_THIS_WITH_YOUR_LEADERBOARD_ID";
var achievementId1 = "REPLACE_THIS_WITH_YOUR_ACHIEVEMENT_ID1";
var achievementId2 = "REPLACE_THIS_WITH_YOUR_ACHIEVEMENT_ID2";
var achievementId3 = "REPLACE_THIS_WITH_YOUR_ACHIEVEMENT_ID3";
var achievementId4 = "REPLACE_THIS_WITH_YOUR_ACHIEVEMENT_ID4";

//
document.addEventListener("deviceready", function(){
	window.game.setUp();

	//callback
	window.game.onLoginSucceeded = function(result) {
		var playerDetail = result;
        alert('onLoginSucceeded: ' + playerDetail['playerId'] + ' ' + playerDetail['playerDisplayName']);
    };	
    window.game.onLoginFailed = function() {
        alert('onLoginFailed');
    };
    window.game.onGetPlayerImageSucceeded = function(result) {
		var playerImageUrl = result;
        alert('onGetPlayerImageSucceeded: ' + playerImageUrl);
    };
    window.game.onGetPlayerImageFailed = function() {
        alert('onGetPlayerImageFailed');
    };	
    window.game.onGetPlayerScoreSucceeded = function(result) {
		var playerScore = result;
        alert('onGetPlayerScoreSucceeded: ' + playerScore);
    };
    window.game.onGetPlayerScoreFailed = function() {
        alert('onGetPlayerScoreFailed');
    };
	//	
    window.game.onSubmitScoreSucceeded = function() {
        alert('onSubmitScoreSucceeded');
    };	
    window.game.onSubmitScoreFailed = function() {
        alert('onSubmitScoreFailed');
    };	
	//	
    window.game.onUnlockAchievementSucceeded = function() {
        alert('onUnlockAchievementSucceeded');
    };  
    window.game.onUnlockAchievementFailed = function() {
        alert('onUnlockAchievementFailed');
    };
    window.game.onIncrementAchievementSucceeded = function() {
        alert('onIncrementAchievementSucceeded');
    };  
    window.game.onIncrementAchievementFailed = function() {
        alert('onIncrementAchievementFailed');
    };
    window.game.onResetAchievementsSucceeded = function() {
        alert('onResetAchievementsSucceeded');
    };	
    window.game.onResetAchievementsFailed = function() {
        alert('onResetAchievementsFailed');
    };
//events
window.facebook.On login succeeded
window.facebook.On login failed
window.facebook.On logout succeeded
window.facebook.On logout failed
window.facebook.On check permissions succeeded
window.facebook.On check permissions failed
window.facebook.On request permissions succeeded
window.facebook.On request permissions failed
window.facebook.On prompt wall post succeeded
window.facebook.On prompt wall post failed
window.facebook.On prompt wall post link succeeded
window.facebook.On prompt wall post link failed
window.facebook.On prompt wall post link this app succeeded
window.facebook.On prompt wall post link this app failed
window.facebook.On publish wall post succeeded
window.facebook.On publish wall post failed
window.facebook.On publish wall post link succeeded
window.facebook.On publish wall post link failed
window.facebook.On publish wall post link this app succeeded
window.facebook.On publish wall post link this app failed
window.facebook.On publish score succeeded
window.facebook.On publish score failed
window.facebook.On request high score succeeded
window.facebook.On request high score failed
window.facebook.On invite succeeded
window.facebook.On invite failed
	
}, false);

//
window.game.login();
window.game.logout();
alert(window.game.isLoggedIn());
window.game.getPlayerImage();
window.game.getPlayerScore(leaderboardId);
//actions
window.facebook.Login
window.facebook.Logout
window.facebook.Check permissions: (publish_actions: need to be reviewed by facebook)
window.facebook.Request permissions: (publish_actions: need to be reviewed by facebook)
window.facebook.Prompt wall post
window.facebook.Prompt wall post link
window.facebook.Prompt wall post link this app
window.facebook.Publish wall post: (publish_actions)
window.facebook.Publish wall post link: (publish_actions)
window.facebook.Publish wall post link this app: (publish_actions)
window.facebook.Publish score: (publish_actions)
window.facebook.Show leaderboard: (publish_actions)
window.facebook.Hide leaderboard: (publish_actions)
window.facebook.Request high score: (publish_actions)
window.facebook.Invite

//
window.game.submitScore(leaderboardId, 5);//leaderboardId, score
window.game.showLeaderboard(leaderboardId);

//
window.game.unlockAchievement(achievementId1);
window.game.unlockAchievement(achievementId2);
window.game.unlockAchievement(achievementId3);
window.game.unlockAchievement(achievementId4);
window.game.incrementAchievement(achievementId1, 2); //achievementId, incrementalStepOrCurrentPercent: Incremental step (android) or current percent (ios) for incremental achievement.
window.game.incrementAchievement(achievementId2, 2);
window.game.incrementAchievement(achievementId3, 2);
window.game.incrementAchievement(achievementId4, 2);
window.game.showAchievements();
window.game.resetAchievements();//only supported on ios

//conditions
window.facebook.Is logined
window.facebook.Is showing leaderboard
*/
```
# Examples #
<a href="https://github.com/cranberrygame/cordova-plugin-share-facebook/blob/master/example/basic/index.html">example/basic/index.html</a>

# Test #

```c
```

# Useful links #

Cordova Plugins<br>
http://cranberrygame.github.io?referrer=github

# Credits #

https://github.com/Wizcorp/phonegap-facebook-plugin/tree/3d52b1eb8a55ebcf8ad10c75d99deedeca0c0fdd
