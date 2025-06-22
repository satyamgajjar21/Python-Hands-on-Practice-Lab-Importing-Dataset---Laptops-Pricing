# Hands-on Practice Lab: Importing Dataset - Laptops Pricing

<p align="center">
  <a href="https://skills.network" target="_blank">
    <img src="https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/assets/logos/SN_web_lightmode.png" width="300" alt="Skills Network Logo">
  </a>
</p>

---

## Estimated Time Needed  
**20 minutes**

---

## Objectives

After completing this lab, you will be able to:

- Import a dataset from a CSV file to a Pandas DataFrame  
- Develop basic insights about the dataset

---

## Setup

We will use the following Python libraries:

- `skillsnetwork` for downloading the dataset  
- [`pandas`](https://pandas.pydata.org/) for data management  
- [`numpy`](https://numpy.org/) for numerical operations  

---

## Data Acquisition

The dataset is available at:

`https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DA0101EN-Coursera/laptop_pricing_dataset_base.csv`

In this lab (running on JupyterLite), you need to download the dataset to the interface using the provided `download()` function before loading it into a DataFrame.

Example:

```python
from pyodide.http import pyfetch
import pandas as pd

async def download(url, filename):
    response = await pyfetch(url)
    if response.status == 200:
        with open(filename, "wb") as f:
            f.write(await response.bytes())

file_path = "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-DA0101EN-Coursera/laptop_pricing_dataset_base.csv"
await download(file_path, "laptops.csv")

df = pd.read_csv("laptops.csv", header=None)
print(df.head())
