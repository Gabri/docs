# Helpers

Jesse includes a variety of helper functions. Many of these functions are used by the framework itself; however, you are free to use them in your own applications if you find them convenient.

Here's how to import helpers:

```py
import jesse.helpers as jh
```

## risk\_to\_qty

Calculates the quantity based on the percent of the capital you're willing to risk per trade.

This is probably the most important helper function that you're going to need in your strategies. You can play around with the formula at [positionsizingcalculator](https://positionsizingcalculator.com).

```py
risk_to_qty(capital, risk_per_capital, entry_price, stop_loss_price)
```

**Properties**:

-   capital: float
-   risk_per_capital: float
-   entry_price: float
-   stop_loss_price: float

**Return Type**: float

**Example**:

```py
def go_long(self):
    # risk 1% of the capital($10000) for a trade entering at $100 with the stop-loss at $80
    qty = jh.risk_to_qty(10000, 1, 100, 80)
    # qty == 5

    self.buy = qty, 100
    self.stop_loss = qty, 80
    self.take_profit = qty, 150
```

TODO...