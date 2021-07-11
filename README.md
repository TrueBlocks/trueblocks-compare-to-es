# trueblocks-compare-to-es

This repo show a comparison between TrueBlocks and Etherscan. We picked 200 random addresses from the approximately 1,800 gitcoin grants and did the following:

1. Request a list of transactions from each of the five EtherScan API endpoints: external, internal, erc20, nfts, and miner. These queries were stored under the `./etherscan` folder (now tarred and zipped). Before creating the files, we remove duplicates because Etherscan's APIs may produce the same record for different APIs.

2. Request the same list of transactions (although we call them appearances) from TrueBlocks. Since there are no duplicates from this query, we don't need to remove dups.

3. Do a 'diff' against the two folders producing the `diffs` folder. Note that in every case, TrueBlocks finds everything EtherScan finds, but in 95% of the cases, Etherscan does not find everything TrueBlocks finds.

4. Next, use the diff files and the TrueBlocks `chifra transactions` routine to figure out why the appearances were found by TrueBlocks but not Etherscan. (We knew why before we looked, but we looked anyway.)

5. Finally, we separate the various reasons into individual folders so as to make analysis easier.

## Results

- For 200 randomly selected addresses, TrueBlocks' `list` endpoint finds more appearances than EtherScan's five endpoints (combined and de-dupped) 93.5% of the time.
  
- Nearly 60% of those additional appearances appear in the transactions' `input` data field. An further 20% of additional appearances show in the log topics (usually as bytes32). Of the remaining 20% of additional appearances, 3/4 appear either in the `trace input` or `trace output` of the transaciton's traces.

- These additional appearances allows TrueBlocks to create 'profit and loss statements' at each transaction for each of the 200 selected addresses. This presages a future of instantanious, every-14-second, permissionless accounting for any Ethereum mainnet address.

- All of TrueBlocks results were produced on a commercially available desktop computer with data aquired only and directly from an OpenEthereum Archive Tracing node. No additional third-party data was used (other than Etherscan to aquired Etherscan's results, obviously).

## Data

We produced three spreadsheets that further detail these results:

[Comparison with EtherScan](https://docs.google.com/spreadsheets/d/1us7d03vDCMu23YCp9z5XOaxQ7FIk88U8FhKL4535-1A/edit#gid=683722752)

[Analysis of Differences](https://docs.google.com/spreadsheets/d/1uz941pXiN8NJriQo3XSDk8zo3ZGIGu1KjmsyHRiRsoM/edit#gid=1729668223)

[Example Account Reconcilations](https://docs.google.com/)
