# Real order-timing source (UCI Online Retail)

The intraday arrival profile (`data/order_timing.csv`) is derived from real order
timestamps rather than hand-set weights. The source is the UCI "Online Retail"
dataset: ~25,900 real online orders with `InvoiceDate` timestamps.

The raw `.xlsx` is large and is not committed. The derived profile
(`data/order_timing.csv`, hour-of-day order shares) is small and committed, so the
twin runs with no download.

## Getting the raw file and rebuilding

```
curl -L -o online_retail.zip https://archive.ics.uci.edu/static/public/352/online+retail.zip
unzip online_retail.zip        # -> "Online Retail.xlsx"
python ../../scripts/fetch_order_timing.py
```

Source: Dua, D. and Graff, C. (2019). UCI Machine Learning Repository, "Online
Retail" (id 352), https://archive.ics.uci.edu/dataset/352/online+retail.

Honest note: this is a real *online-retail* ordering curve (a midday peak, tailing
off by evening), used as a real, observed intraday shape. It is not q-commerce
specific - Indian quick-commerce skews later - so the twin keeps its synthetic
bimodal profile available for comparison. What is real is that the arrival shape
comes from observed orders.
