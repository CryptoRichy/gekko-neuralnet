
# zuki_nn
Gekkowarez team update:

We've worked with numerous machine learning libraries from Synaptic, Neotaptic and thought we'd take a look at a community Strategy which was created by SirTificate (and based on https://github.com/cloggy45/Gekko-Bot-Resources/blob/master/gekko/strategies/mounirs-ga-version-2.js by Mounir). 

Because we had a bunch of code lying around for storing and retrieving a trained neural net it was pretty quick to add. 

# Install
copy the file(s) from /strategies/ into the strategies folder of your gekko install
copy the file(s) from /toml/ into the /config/strategies/ folder of your gekko install

Install the modules in your gekko folder:
`npm install convnetjs mathjs`fs

# Usage / Configuration

Add the following section to your config file:

config.filewriter = {
  nnfilepath: __dirname+"/nn_files/" //encure you have created gekko/nn_files folder
};

For consoles setup create the following entry in your config file:
config.zuki_nn = {
	threshold_buy : 1.0,
	threshold_sell : -1.0,
	learning_rate : 0.01,
	momentum : 0.1,
	decay : 0.01,
	stoploss_enabled : false,
	stoploss_threshold : 0.85,
	hodl_threshold : 1,
	price_buffer_len : 100,
	min_predictions : 1000	
}


If you use the UI then clone / rename it will reference the toml file.

```javascript

// the treshold for buying into a currency. e.g.: The predicted price is 1% above the current candle.close

threshold_buy = 1.00

// the treshold for selling a currency. e.g.: The predicted price is 1% under the current candle.close
threshold_sell = -1.00

// The length of the candle.close price buffer. It's used to train the network on every update cycle.
price_buffer_len = 100

// The learning rate of net
learning_rate = 0.01


// learning speed
momentum = 0.9
decay = 0.01

//minimum number of prictions until the network is considered 'trained'. History size should be equal
min_predictions = 1000

//enables stoploss function
stoploss_enabled = false

//trigger stoploss 5% under last buyprice
stoploss_threshold = 0.95

```


