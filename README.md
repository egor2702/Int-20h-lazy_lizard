# INT20H lazy_lizard
This repo contains or attempt at the solution of the test task for INT20H.

In `preprocess.ipynb` you can find feature engineering and some initial filtering of the dataset.
`analysis.ipynb` contains a more in-depth, you guessed it, analysis, with multiple technics taken to find the features that correlate the most and the least with the cancellation of the Premium Subscription.

The first approach is, obviously, correlation, which shows the following:
|Feature Name (Largest Absolute Values)|Correlation Coefficient||Feature Name (Smallest Absolute Values)|Correlation Coefficient|
|:---|:---:|---|:---|:---:|
|Chat Conversation Started|0.389||Google (platform)|0.001|
|Chat Opened from Menu|0.381||Calculator Used|-0.003|
|Transaction Refund|0.287||Sign up (Facebook)|0.006|
|Subscription Premium Renew|-0.158||Other (platform)|-0.007|
|Subscribed for less than a month|0.143||Sign up (Email)|-0.021|

All the positive correlation is attributed to the obviously negative events: starting a conversation with support, refunding a transaction, not using the app for a long period of time (which could mean that the UX wasn't satisafactory, or this simply wasn't the solution that particular client needed). Whereas the only negative value indicates that users who choose to renew their subscription are less likely to later on cancel, which is a pretty logical conclusion.

Next we looked at mutual information scores:
|Feature Name (Largest Values)|MI Score||Feature Name (Smallest Values)|MI Score|
|:---|:---:|---|:---|:---:|
|Chat Conversation Started|0.182||Subscribed for less than a month|0.0|
|First to Last Event (hours)|0.115||No Card Added|0.0|
|Chat Opened from Menu|0.097||Sign up (Facebook)|0.0|
|Wallet Opened|0.073||Didn't try to add a vehicle|0.0|
|Other (platform}|0.059||Sign up (Email)|0.0|

Lastly we employed a Random Forest, which assigned the following feature importances:
|Feature Name (Largest Values)|Feature Importance||Feature Name (Smallest Values)|Feature Importance|
|:---|:---:|---|:---|:---:|
|Chat Conversation Started|0.218||No Card Added|0.001|
|Chat Opened from Menu|0.112||Didn't try to add a vehicle|0.002|
|First to Last Event (hours)|0.107||Google (platform)|0.002|
|Wallet Opened|0.065||Payment Method Added (Venmo)|0.003|
|Transaction Refund|0.056||Account Setup Skip|0.003|

Now these ones are a bit trickier to interpret, so let's visualize:
(lol add the image)
