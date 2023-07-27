# NFT-Price-Prediction

Non-Fungible Token (NFT) is a digital property used to represent objects such as art,
collectibles, and in-game items. These have become a popular means for creators to sell their
artistic content and as a means of investment. NFT pricing is largely driven by speculations
rather than an underlying value such as earnings. Its marketplace is identified to be
unpredictable with highly skewed and uncertain returns along with supreme growth. Thus, the
investment in NFT is associated with high risks due to its volatility. Due to its volatility,
forecasting on future values of NFT has become an important task for investors' financial
security and their investments.
With the rise of social media, such as Twitter, it has emerged as grounds for NFT holders and
creators to navigate and form public opinion on NFT. According to behavioral finance theories,
"people are more likely to make decisions based on overconfidence bias and herd behavior
when faced with uncertainty (Sawhney et al., Findings 2022)." Thus, incorporating social media
can be useful in carrying out analysis and creating prediction models of the NFT market. There are
many challenges that cause hindrances in selecting the right NFTs to feature in auctions for
some organizations which is why they are researching this area to make their task easier.

## Problem Statement
Here we will be building a machine-learning model capable of predicting prices of NFTs based on social media activity and some group attributes.

### Dataset
We downloaded the dataset from the following link: https://bitgrit.net/competition/17
It's a competition hosted by Bitgrit. The dataset can be accessed from the resources tab by
creating an account on bitgrit and registering for this competition. We downloaded the dataset
zipped file and unzipped it in our local system.

#### collections.csv -> data about collections that are in the training and prediction dataset.
1. collection_id: ID to identify the collection and the NFTs of the collection
2. total_supply: total number of NFTs in the collection
3. creation_date: creation date of the collection in the marketplace
4. verification_status: status of verification of the collection in the marketplace
5. n_of_traits: number of particular traits the NFTs in the collection can have
6. contract_type: type of contract in the marketplace
7. seller_fees: fees that the seller receives for transactions
8. platform_fees: fees that the marketplace receives for transactions
9. openrarity_enabled: whether the collection uses OpenRarity to calculate a rarity score and
rank for the NFTs in the collection.
10. has_website: whether the collection has a website or not
11. has_own_twitter: whether the collection has its own Twitter account or not
12. has_discord: whether the collection has a Discord channel or not
13. has_medium: whether the collection has a Medium account or not

#### collections_twitter_stats.csv: basic stats about Twitter accounts of collections or creators of the collections.
1. collection_id: ID to identify the collection and the NFTs of the collection
2. n_tweets_in_range: number of tweets in the relevant timeframe
3. avg_likes: average number of likes per tweet
4. avg_replies: average number of replies per tweet
5. avg_retweets: average number of retweets per tweet
6. min_likes: minimum number of likes per tweet
7. min_replies: minimum number of replies per tweet
8. min_retweets: minimum number of retweets per tweet
9. max_likes: maximum number of likes per tweet
10. max_replies: maximum number of replies per tweet
11. max_retweets: maximum number of retweets per tweet

#### nfts_train.csv: NFT data from all collections, which can be used to train price prediction model.
• global_index: global ID of the NFT to identify it considering all collections
• nft_id: ID of the NFT to identify its particular collection
• collection_id: ID of the collection the NFT belongs to as per collections.csv file
• rarity_score: estimated rarity score within the collection
• openrarity_score: OpenRarity score if it is enabled (see 1)
• openrarity_rank: OpenRarity rank within the collection if it is enabled (see 1)
• openrarity_max_rank: OpenRarity maximum rank of the collection if it is enabled {see 1)
• last_sale_date: approximated date of the last sale of the NFT
• last_sale_price: price at which the NFT was last sold for (target variable)

#### nfts_predict.csv: NFT data from all collections, which should be predicted using trained model.
1. global_index: global ID of the NFT to identify it considering all collections
2. nft_id: ID of the NFT to identify its particular collection
3. collection_id: ID of the collection the NFT belongs to as per collections.csv file
4. rarity_score: estimated rarity score within the collection
5. openrarity_score: OpenRarity score if it is enabled (see 1)
6. openrarity_rank: OpenRarity rank within the collection if it is enabled (see 1)
7. openrarity_max_rank: OpenRarity maximum rank of the collection if it is enabled (see 1)
8. last_sale_date: approximated date of the last sale of the NFT
9. 
There are four datasets in csv format with the above-listed attributes. The plan with
these datasets is to analyze and process to see whether there is a recognizable pattern behind
the fluctuation of NFT pricing. We will build a forecasting model based on a select group of their
attributes, which are publicly accessible, and based on their social media activity.
