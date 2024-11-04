## Preprocessing Steps

We plan to normalize the columns in our dataframe using min max normalization because most of the data doesn't appear to be normally distributed. While some of the columns in the dataset appear to follow a normal distribution, the majority of them are either skewed or bimodal, so we cannot use the Z score to standardize all of the data. With the data in the given form, the scale of the data is rather unknown since when we downloaded it the data was already scaled in some fashion, having some clear features that don't represent raw numbers, for example an observation with 'infant deaths' of -0.56.

We do not need to deal with missing data (Nan data) because it appears we have no missing data, but looking at some of the distributions it seems that we have some outliers so we will do our best to remove those.
