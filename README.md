# tech-nonprofit-salaries

## Objective

One of the many challenges for a tech nonprofit is determining fair compensation. Nonprofit salaries are sterotypically lower than for-profit salaries, of course. But on the other hand, you might expect that there would be upward pressure on tech nonprofit salaries because the job responsibilities are often closer to those in a for-profit tech startup than in a traditional nonprofit, and because equity can't be part of the compensation package.

So, I analyzed a bunch of open data on C-level salaries at tech nonprofits. Hopefully this helps the tech nonprofit ecosystem understand what's been going on with compensation!


## Comments or suggestions?

Please fork and play around, make an issue or PR, or say hi on twitter [@windupanna](https://twitter.com/windupanna) :)


## Data sources

*Tech nonprofits*: The wonderful tech nonprofit accelerator [Fast Forward](http://www.ffwd.org/) has a [list of tech nonprofits](http://www.ffwd.org/tech-nonprofits/).

*Nonprofit salary data*: The IRS requires that 501c3 nonprofits submit salary data for board members, officers, and highly paid employees on their 990F tax forms. These tax forms are available on many organizations' websites, on [GuideStar](http://www.guidestar.org/), and in an [AWS S3 bucket](https://aws.amazon.com/public-datasets/irs-990/); none of these sources are exhaustive.


## 2016 version

For every org on the Fast Forward list, I created a list of 990F files to collect from S3 (`output/metadata.csv`), using the EINs on GuideStar to disambiguate between orgs when the name on the Fast Forward list doesn't match the name in the AWS dataset.

For each 990F in the list, I collected the actual 990F data and wrote it to `output/comp_data_raw.csv`. This file contains these columns: org name, city, state, EIN, URL of the 990F on S3, tax year, year the org was formed, submission time of the 990F, number of employees, total revenue, job title, and compensation.

For richer data analysis, I also assigned some extra features to each observation. Most importantly, each role was assigned to one or more job groups (Chief Executive Office/Executive Director, Chief Technology Officer, Chief Operating Officer, Chief Financial Officer, Business Development, President, Chief Marketing Officer, Chief Development Officer, Board, Founder, or uncategorized). There are also added features for whether each job group was present in that org in that year, boolean features for location, etc. The expanded dataset is at `output/comp_data_features.csv`.

To get an environment where you recreate this dataset:

```
git clone https://github.com/aschn/tech-nonprofit-salaries.git
pip install -r requirements.txt
ipython notebook
```

Run the contents of `1_tech_nonprofit_irs_metadata.ipynb` to scrape the AWS 990 data, create ~180M of data in `irs-form-990/index_201*.csv`, and recreate `output/metadata.csv`.

Run the contents of `2_tech_nonprofit_irs_comp_features.ipynb.ipynb` to recreate `output/comp_data_raw.csv` and `output/comp_data_features.csv`.


To play with the data, open `output/comp_data_features.csv` in your data analysis tool of choice.


## 2015 version

For every org on the Fast Forward list, I attempted to find 990F tax forms by hand on the org's website
and/or on the nonprofit data source [GuideStar](http://www.guidestar.org/).

If I could find 990Fs, I checked recent ones to see if a CTO-like or CFO-like position was listed.
(CTO-like positions included job titles like "Director of Engineering" and "Chief Software Architect",
while CFO-like positions included job titles like "Director of Finance" and "VP Finance and Administration".)

If either a CTO or a CFO was compensated, then I logged the following pieces of data for all available years:
organization name, job title, job category, salary,
tax year, organization age in tax year, location of organization headquarters,
and link to the 990F pdf document.
I also logged compensation for CEO-like and COO-like positions in years when a CTO and/or CFO was compensated.

The data set is available on Google Sheets at https://docs.google.com/spreadsheets/d/1u3aH86lFRL4pLb0qV2JQFzlmYd_TduhPlwuIwOv_UXk/
