# ITBC 2019
Shopee Competition 2019-10-20

# Getting Started
## Instructions
* For each round `n`, download data from kaggle and place them into `round_n/data` folder
* If only 1 main data file, change the value for variable `SRC_DATA` to the data file path in each `round_n.ipynb`
* Use filename of `submission.csv` for the file to be submitted (if there is only 1 submission data file)

## Helper Libraries
* `pip install kaggle` to get kaggle cli
* to submit from terminal, use the below command from `round_n` folder:
	* `kaggle competitions submit -c shopee-competition-page -f submission.csv -m "submission message from cli"`
