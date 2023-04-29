# MBS Deferred Asset

The MBS Deferred Asset model is used for fair value assets that have been transferred to the Canada Housing Trust (CHT) through participation in the Canada Mortgage Bond (CMB) program. In particular, the model calculates the fair value of the retained interest of the MBS.

The model is a simple static cash flows model for the underlying MBS. The simplicity
is possible due to the assumption that the prepayments of the underlying pool are not dependent on changes in interest rates. Generally, prepayments do depend on interest rates, and this is particularly true for US mortgages. 

The introduction of interest rate dependent prepayments (and hence cash flows) requires the use of an dynamic interest rate model, and would complicate the model substantially. However, for the Canadian market it is deemed not nearly as important, and hence prepayments are assumed to be constant.

Firstly, we will review the basic equations governing cash flows from the MBS. The mortgage payment in month n made by the mortgagee is provided. For the MBS, rn is the weighted average interest rate of mortgages in the pool, and this value changes during the life of the MBS as mortgages prepay. 

The MBS pay a fixed coupon cn, specified by the contract. The model values the difference between the actual interest payments based on rn and cn, minus a fixed servicing of 25 bps. 

We then simply present value these cashflows to arrive at a valuation. The discount curve is the CAD swap curve, with spot rates and simple compounding for the 1 year and under term points, and swap rates for longer terms

For the variable rate pools, we need to specify what rn and cn are. These rates depend on the prime rate, and the current prime rate is an input into the spreadsheet model. For each pool, two different spreads are also input: the spread to prime (sp) and the MBS spread over the one month spot rate (sy). In this case, r1 = p + sp, while c1 = y1M + sy, where p is the current prime rate and y1M is the current one month spot rate. 

For the future months, the model calculates the one month forward rates, and “models” the prime rate as 1.75% above that forward rate. We make the same assumption that the prepayments are primarily refinances and not partial prepayments. This means that the prepayments effectively reduce the cash flows, not the amortization of the MBS. However, there is a crucial difference with the submitted model and conventional MBS models, in that the model assumes the prepayments are not rate dependent. This greatly simplifies the model, since a dynamic model is not required.

Reference:

https://finpricing.com/FinPricing-ProductBrochure.pdf
