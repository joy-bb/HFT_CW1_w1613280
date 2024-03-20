# LIQUIDATION WITH TEMPORARY AND PERMANENT PRICE IMPACT
## About
In high-frequency trading, an agent may use market orders to liquidate shares with both temporary and permanent price impact, but this can be a challenging task due to the speed and complexity of the market.
A market order is an order to buy or sell a security at the current market price. It is the simplest and fastest way to execute a trade, but it can also result in significant price impact if there is not enough liquidity in the market to absorb the order.
To liquidate shares with both temporary and permanent price impact, an agent must carefully balance the speed and size of their market orders to minimize market impact and achieve the desired execution price. This can involve using sophisticated algorithms and trading strategies to analyze market conditions and adjust trading parameters in real-time.

### 1. Agent’s objective/performance criterion
![image](https://github.com/joy-bb/HFT_CW1_w1613280/assets/71431452/f9481279-3f0e-4461-9a30-9392a3e8d548)
![image](https://github.com/joy-bb/HFT_CW1_w1613280/assets/71431452/2c9593e9-4644-4614-845c-006947509882)

### 2. Processes explanation: The value function, HJB with terminal condition, Optimal trading speed and accordant Inventory
![image](https://github.com/joy-bb/HFT_CW1_w1613280/assets/71431452/95e3a186-0171-4037-a6c2-9be9357be7c1)
![image](https://github.com/joy-bb/HFT_CW1_w1613280/assets/71431452/67eda45f-ac69-463d-9ab1-a5665ea339bb)
![image](https://github.com/joy-bb/HFT_CW1_w1613280/assets/71431452/85c87e31-eecf-4444-aeb6-fbc8664a143b)
![image](https://github.com/joy-bb/HFT_CW1_w1613280/assets/71431452/bde03793-2b22-4141-86ca-9d3a3c34c0e9)

### 3. Application with specific case:
With the explanation provide above, this section will apply python code to illustrate the liquidation stock with both temporary and permanent price impacts on particulate parameters set ups as below:
![image](https://github.com/joy-bb/HFT_CW1_w1613280/assets/71431452/674388d4-c092-4fa0-b696-1a016098fb09)

To liquidate 10-million shares of stocks on 5.000 trading times with provided parameters of k, b, alpha, phi and sigma. The trading speed is plotted as the following figure:
![image](https://github.com/joy-bb/HFT_CW1_w1613280/assets/71431452/ac3c61b0-499d-4dc7-9b4f-7f39dec1e69f)
As the time increases, the number of shares per trade will decrease over time. The number of shares per trade can only reach the highest of around 4.500 shares on the beginning, then go down gradually to 2.000 after 0.4 second and reach 1.000 after 1 second. 
With the plotted trading speed, the according inventory is plotted as below:
![image](https://github.com/joy-bb/HFT_CW1_w1613280/assets/71431452/c16fbfcd-541c-4f7e-8c7d-e4c713a61940)
At the beginning, the inventory is the highest equal total of shares need to be liquidated – 10 million. With very higher trading speeds at the first 0.4 seconds, inventory only has around 4 million shares left and then go down to 0 with lower speeds.  
Both trading speed and inventory has the similar pattern of downwards and this is because the strategy is to minimize both permanent price impact and temporary impact by balancing speed, size and market impact to achieve the desired execution price while minimizing slippage and other trading costs. The agent’s strategy aims at minimize permanent price impact by using a more aggressive trading strategy that aims to quickly liquidate their position using larger market orders. However, this strategy can also increase market impact and result in larger slippage costs, so it must be carefully balanced against the need for speed. At the same time, the agent also wants to minimize temporary price impact, by using a slow trading strategy that gradually liquidates their position over time, using smaller market orders to avoid overwhelming the market and causing sudden price movements. This can help to spread out the market impact of the orders and minimize slippage.

### Change of the investor's inventory for various levels of the running penalty as alpha changes
Considering two values of terminal liquidation penalty:  and  (value of 100 is used in the code), with different level of running inventory penalty, the inventory and trading speeds are plotted as below:

![image](https://github.com/joy-bb/HFT_CW1_w1613280/assets/71431452/1d9c96a0-8004-4e1f-9cc3-0d10948a46bd)

![image](https://github.com/joy-bb/HFT_CW1_w1613280/assets/71431452/a992091e-272b-434e-942d-91ca4038529c)
The running inventory penalty (phi) is a cost that represents the penalty for holding inventory. When the running inventory penalty decreases and reaches zero, it means that there is no cost associated with holding inventory, and traders can hold inventory for as long as they want without incurring any penalty costs. As a result, when the running inventory penalty decreases and reaches zero, the optimal trading strategy for a trader would be to execute trades more slowly and patiently, in order to minimize the impact of trading costs and maximize profits. This could involve using less aggressive trading strategies, such as limit orders, that allow traders to enter and exit the market more slowly and at more favorable prices. From the figure 10 and 11, with no running penalty   (valued 10e-10 in the code), the strategy is a straight line. When the value   increases, the strategy results in a curve and the curves is getting more and more pronounced with the higher running inventory penalty, mean the investors want to liquidate the shares as faster as the cost of holding inventory increases. This rule applies the same with despite different value of alpha as in figure 10 and 11 (trading speed starts highest at 7 for  = 0.1 then around 2.2 for  = 0.01, and around 1 for  nearly reach zero).
The terminal liquidation penalty (alpha) is a cost that represents the penalty for not completely liquidating a position at the end of a trading horizon. When the terminal liquidation penalty increases and reaches infinity, it means that there is an infinite cost associated with not completely liquidating a position, and traders will have to completely liquidate their position at the end of the trading horizon, regardless of the cost. This explain the different between figure 10 and figure 11. In figure 10, even with different value of phi, the inventory after time horizon can be varies (around 0.2 for  = 0.001 and 0.1 for  = 0.01) but not all reach to 0 like figure 11. In figure 11, the is no inventory left despite value of   because the cost for not completing liquidation is infinite which far outweighs any potential trading profits.



