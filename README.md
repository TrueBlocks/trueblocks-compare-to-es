# trueblocks-compare-to-es

Without too much explaination, this repo show a comparison between TrueBlocks and Etherscan. We picked 200 random addresses from the approximately 1,800 gitcoin grants and did the following:

1. Request a list of transactions from each of the five EtherScan API endpoints: external, internal, erc20, nfts, and miner. These queries were stored under the `./etherscan` folder (now tarred and zipped). Before creating the files, we remove duplicates because Etherscan's APIs may produce the same record for different APIs.

2. Request the same list of transactions (although we call them appearances) from TrueBlocks. Since there are no duplicates from this query, we don't need to remove dups.

3. Do a 'diff' against the two folders producing the `diffs` folder. Note that in every case, TrueBlocks finds everything EtherScan finds, but in 95% of the cases, Etherscan does not find everything TrueBlocks finds.

4. Next, use the diff files and the TrueBlocks `chifra transactions` routine to figure out why the appearances were found by TrueBlocks but not Etherscan. (We knew why before we looked, but we looked anyway.)

5. Finally, we separate the various reasons into individual folders so as to make analysis easier.

## Results

We produced two spreadsheets to show the data:

[Comparison with EtherScan](https://docs.google.com/spreadsheets/d/1us7d03vDCMu23YCp9z5XOaxQ7FIk88U8FhKL4535-1A/edit#gid=683722752).

[Analysis of Differences](https://docs.google.com/spreadsheets/d/1uz941pXiN8NJriQo3XSDk8zo3ZGIGu1KjmsyHRiRsoM/edit#gid=1729668223)
