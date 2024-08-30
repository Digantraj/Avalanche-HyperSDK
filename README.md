# Avalanche HYPERSDK PROJECT

This project uses HyperSDK that provides the ability to create a custom virtual machine, which offers complete control over a custom blockchain. By using the HyperSDK, we have full control over the rules and functionality of your chain, allowing us to create a custom blockchain that is tailored to your startup's specific needs. 


## Description 
```consts/consts.go``` contains the constants that is accessible across the hyperVM. The HRP, Name, and Symbol constants define information about the TokenVM, including its Human-Readable Part (HRP), name, and symbol.
```GO
const (
	// TODO: choose a human-readable part for your hyperchain
	HRP = "mynameisdigant"
	// TODO: choose a name for your hyperchain
	Name = "digant"
	// TODO: choose a token symbol
	Symbol = "dr"
)
```

## Steps of Execution
This project is execute on WSl on windows and GO installed inside wsl.<br>
1) run ```git clone [https://github.com/Digantraj/Avalanche-HyperSDK]```
2) run ```cd avax-advance-mod-2```
3) Extract the ```Avalanche hyperSDK project```
4) cd ```'.\Avalanche hyperSDK project\' ```
5) In terminal run command ```MODE="run-single" ./scripts/run.sh``` and this will start our machine with 1 subnet and for 2 subnet run ```./scripts/run.sh```. after this command output will look like.
```javascript
Ran 4 of 4 Specs in 81.284 seconds
PASS
cluster is ready!
avalanche-network-runner is running in the background... 

use the following command to terminate:

killall avalanche-network-runner
```
6) To start interaction run ```./scripts/build.sh```. output will be :
```javascript
/scripts/build.sh
Building tokenvm in ./build/tHBYNu8ikqo4MWMHehC9iKB9mR5tB3DWzbkYmTfe9buWQ5GZ8
Building token-cli in ./build/token-cli
```
This command will put the compiled CLI in ./build/token-cli.
<b>NOTE- default address is ```token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp```</b>

7) Lastly, we'll need to add the chains we created and the default key to the token-cli. run command:
```javascript
./build/token-cli key import demo.pk
./build/token-cli chain import-anr
```
chain import-anr connects to the Avalanche Network Runner server running in the background and pulls the URIs of all nodes tracking each chain you created..

## Creation and Minting process
### Step 1 Asset Creation
To create an assest run the command:
```javascript
./build/token-cli action create-asset
```
Enter the metadata (eg:DigiCoin) and confirm
output looks like:
```javascript
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: 2TjbjoVxp8E5foRPTPZDqwSYKW4DywRdjQc93GxfZa7iQ9LsEA
metadata (can be changed later): DigiCoin
✔ continue (y/n): y█
✅ txID: ueybUhparatcswjoRheVyuhsTHyHDYR8PvDkWDaz7mjmi7rjo
```
<b>NOTE - txID is the assetID of your new asset.</b>

### Step 2 Minting of asset
To mint the created assest run command:
```javascript
./build/token-cli action mint-asset
```
enter the assetID then enter the receipient then enter the amount and continue.
It would look like:
```javascript
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: 2TjbjoVxp8E5foRPTPZDqwSYKW4DywRdjQc93GxfZa7iQ9LsEA
assetID: ueybUhparatcswjoRheVyuhsTHyHDYR8PvDkWDaz7mjmi7rjo
metadata: DigiCoin supply: 0
recipient: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
amount: 10000
continue (y/n): y
✅ txID: mpP4RSfUyMm9GCFn1NKzNr6ES1Hj4EswwCWbVJWxvP5dkwp62
```
### Step3 check balance
run the command:
```javascript
./build/token-cli key balance
```
and enter the assetID of the token and output will be like:
```javascript
database: .token-cli
address: token1rvzhmceq997zntgvravfagsks6w0ryud3rylh4cdvayry0dl97nsjzf3yp
chainID: 2TjbjoVxp8E5foRPTPZDqwSYKW4DywRdjQc93GxfZa7iQ9LsEA
assetID (use TKN for native token): ueybUhparatcswjoRheVyuhsTHyHDYR8PvDkWDaz7mjmi7rjo        
uri: http://127.0.0.1:49498/ext/bc/2TjbjoVxp8E5foRPTPZDqwSYKW4DywRdjQc93GxfZa7iQ9LsEA        
metadata: DigiCoin supply: 10000 warp: false
balance: 10000 ueybUhparatcswjoRheVyuhsTHyHDYR8PvDkWDaz7mjmi7rjo
```
### Transfer assets
spilt terminal and in 1st run the command 
```javascript
./build/token-cli chain watch
```
and from the listed chainID enter the desired index of the chainID and it will start live watching of the blockchain.
enter 1 and execute it
in second terminal run
```javascript
./build/token-cli action transfer
```

### Closing 
run the command 
```javascript
killall avalanche-network-runner
```
This will close the blockchain we just deployed.

## License

This project is licensed under the MIT License.

## Authors

- **Digant Raj**  
  GitHub: [@Digant](https://github.com/Digantraj)
