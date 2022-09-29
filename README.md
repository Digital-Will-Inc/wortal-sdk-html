# Wortal SDK for HTML5 Games

## Installation
1. Add `wortal.js` and `intl-data.json` to the root of your game directory, at the same level as `index.html`
2. Change the `GAME_NAME` in `wortal.js` to match your game's name.
3. Add the following `<div>` in the `<body>` of your `index.html`

`<div class="loading-cover" id="loading-cover" style="background: #000; width: 100%; height: 100%; position: fixed; z-index: 100;"></div>`

4. Add calls for ads and analytics in your game code
5. Create a `.zip` archive of the game with the `index.html` at the root
6. Upload build to the Wortal dashboard

## How to Use

### Interstitial Ads
Interstitial ads are convenient to show to players at certain milestones throughout your game. Ex: Player finishes a level, player levels up, etc.

```js
showInterstitial(placement, description, {
    beforeAd: function () {
        // Pause game here
    },
    afterAd: function () {
        // Resume game here
    },
});
```

### Rewarded Ads
Rewarded ads can be used to offer the player bonuses or other incentives during the game. These ads are longer and require the player to watch the ad in its entirety to receive the reward, but are optional.

```js
showRewarded(description, {
    beforeAd: function () {
        // Pause game here
    },
    afterAd: function () {
        // Resume game here
    },
    adDismissed: function () {
       // Don't reward - skipped ad
    },
    adViewed: function () {
       // Reward the player for watching the ad
    },
});
```

### Analytics
The analytics API can be used to track in game events to get a better understanding of how players are interacting with the game.

```js
// Logs the beginning of a level and starts the level timer.
logLevelStart(level);

// Logs the end of a level and records the time played if level matches the last logLevelStart call.
logLevelEnd(level, '100', true);

logLevelUp(level);
logScore(score);

// Logs the player's choice when offered different options.
// This can be useful for determining which characters are more popular, or paths are more commonly taken, etc.
// This can be a powerful tool for balancing the game and giving the players more of what they enjoy.
logGameChoice(decision, choice);
```
