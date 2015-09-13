# tech-nonprofit-salaries

## Objective

One of the many challenges for a tech nonprofit is determining fair compensation.
Nonprofit salaries are sterotypically lower than for-profit salaries, of course.
But on the other hand, you might expect that there would be upward pressure on tech nonprofit salaries because
the job responsibilities are often closer to those in a for-profit tech startup than in a traditional nonprofit,
and because equity can't be part of the compensation package.

So, I analyzed a bunch of open data on C-level salaries at tech nonprofits (specifically CEO, CTO, COO, and CFO).
Hopefully this helps the tech nonprofit ecosystem understand what's been going on with compensation!

## Comments or suggestions?

Please fork and play around, or get in touch at anna@WattTime.org

## Data collection

The wonderful tech nonprofit accelerator [Fast Forward](http://www.ffwd.org/) has a [list of tech nonprofits](http://www.ffwd.org/mapping-out-tech-nonprofits).
For every org on this list, I attempted to find 990F tax forms on the org's website
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

## Data analysis

In progress in the ipython notebook in this repo!
Click on the ipynb file to view the graphs,
or clone and run `ipython notebook` to run the code yourself.
