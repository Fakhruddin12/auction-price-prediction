# Source inputs

The first notebook expects the original listings CSV at `market_listings_new.csv` in its working directory. Open Jupyter from `notebooks/` and place the separately supplied source dataset there, or change its `RAW_DATA_PATH` setting explicitly. Do not add the source CSV to Git without confirmed redistribution rights. The EDA notebook writes `cleaned_tractors.csv` for the second notebook. Re-running requires the same source vintage to reproduce the reported sample construction. A frozen split and training-only transformations are defined by the modelling notebook.
