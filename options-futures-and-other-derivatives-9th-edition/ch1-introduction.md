## CH1 - Introduction
- Derivative
  - a financial instrument whose value depends on (or derives from) the values of other, more basic, underlying variables.
  - credit crisis in 2007: derivatives created from portfolios of risky mortgages in US using securitization -> house prices declined -> derivative products became worthless
  - clearing house: to sort out the creditworthiness between two traders by taking care of credit risk (by requring each of them to deposit deposit funds, aka margin)
- Traded on
  - Exchange  
    - Open Outcry System: traditionally derivatives exchanges
    - Electronic Trading: leading to a growth in HFT and algorithmic traiding
  - OTC (Over-the-counter)
    -  CCP (Central Counterparty): an equivalence of exchange clearing house
      -  stands between the two parties to the derivatives transaction
    - Banks as market makers (for commonly traded traded instruments)
      - prepared to quote a bid price and an offer price at the same time
    - Largely unregulated before hte failure of Lehman Brothers
      - since then, an improvement of the transparency of OTC markets and market efficienct, as well as reduction of systemic risk is deployed
    - transaction size in OTC >> exchange traded market
- Forward Contracts
  - Contrarily to Spot Contracts, it is an agreement to buy or sell an asset at a certain future time for a certain price, traded in the OTC
  - A long position vs. a short position
    - long: agrees to buy the underlying asset on a certain specified futrue date for a certain specified price (長頭寸, 多頭)
    - short: agrees to sell (短頭寸, 空頭)
  - Popular on FX
    - BID 買入 | OFFER 賣出
    - can be used to hedge foreign currency risk
  - An Example: USD/GBP (quote is number of USD per GBP)
    - |  | Bid | Offer |
      |---|---|---|
      | Spot | 1.5541 | 1.5545 |
      | 6-month forward | 1.5526 | 1.5532 |
    - A forward contract obligated the corporation to buy 1 million GBP for $1553200
    - If the spot exchange rate rose at the end of the 6 months, it would enable the 1 million pounds to be purchased at a lower exchange rate
      - thus, the payoff from a long position in a forward contract on one unit of an asset is $S_T-K$
        - where K is the delivery price and S is the spot price at maturity
        - could lead to a negative value when the spot price fell at the end of the 6 months
      - similarly, the payoff from a short position in a forward contract on one unit of an asset is $K-S_T$
    - It costs nothing to enter into a forward contract, so the payoff is also the trader's total gain/loss
  - Another example: Forward prices and spot prices
    - Consider a stock that pays no dividend and is worth $60. You may borrow/lend for 1 year at 5%. What should the 1-year forward price of stock be?
      -  Ans: $60*1.05 = $63
      -  Say it's more than this (e.g. $67), then I could borrow $60 now, buy the stock at $60, and sell forward for $67. After paying off the loan, the net profit is $67 - $63 = $4
      -  Say it's less than this (e.g. $58), the stock holder would sell the stock for $60 now, invest the money at 5% to earn 3%, and then use the $63 to buy it back for $58 after 1 year, resulting in $5 better off.
- Future Contracts
  - Unlike forwards, normally traded on exchange
  - The future price is determined by the laws of supply and demand. If more traders want to go long than to go short, the price goes up, and vice versa.
- Options
  - Traded both onexchanges and OTC
  - call option
    - gives the holder the right to buy the underlying asset by a certain date for a certain price
  - put option
    - gives the holder the right to sell the underlying asset by a certain date for a certain price
  - strike
    - the price in the contract, aka the exercise price
  - date
    - the maturity or expiration date
  - European options can be exercised only on the expiration date itself; it's more easily analyzed
  - American options are more in amount; some properties are deduced from those of its European counterpart
  - There is a cost to acquiring an option, whereas it costs nothing to enter into a forward or futures
  - Exercise
- Hedgers, Speculators, and Arbitrageurs
  - Hedgers
    - use derivatives to reduce the risk that they face from potential future movements in a market variable
  - Speculators
    - use derivatives to bet on the future direction of a market variable
  - Arbitrageurs
    - take offsetting positions in two or more instruments to lock in a profit     