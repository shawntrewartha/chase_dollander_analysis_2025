# Chase Dollander: How His Talents Didn't Lead to Success in 2025
A Statcast-driven look at Chase Dollander's rookie-year home/road split, digging into why his ERA cratered at Coors Field (9.98 at home vs. 3.49 on the road)
despite a talented pitch mix. Companion analysis to the article found on blakestreenbanter.com

> **Full Article -** https://blakestreetbanter.com/2026/03/13/chase-dollander-pitch-analysis/

## Background
Dollander's fastball graded out as one of the more punishing pitches at Coors — it loses about 2 inches of induced break at altitude, and hitters slugged .769
against it at home versus .356 on the road. His cutter was even more extreme (.905 SLG at Coors vs. .348 on the road) before an offseason grip/spin adjustment
added 60 rpm and roughly half an inch of extra movement, which showed up in a 29% whiff rate that spring. His curveball was the one pitch that actually held
up — and even improved — at altitude (.207 SLG overall, .229 at Coors vs. .179 on the road, with a 35.7% whiff rate).

The takeaway from the article is that Dollander's stuff isn't the problem — his pitch mix is. Leaning on the fastball at altitude and using the cutter before
the offseason fix produced results roughly in line with what the pitch-movement data says should happen; leaning more on the curveball, and pitching the
fastball up rather than letting it "graze the top of the zone," is the proposed fix.

This repo builds that home/road dataset directly from Statcast: pitch movement, plate location, and outcome data split by whether the game was at Coors, to
check the article's pitch-by-pitch claims against the underlying numbers.

## Repo structure
notebook/chase_dollander_analysis.ipynb — main analysis notebook: data cleaning, barrel rate by count/pitch, cutter investigation, heat maps, and home/road
splits sample_data/savant_through_2025_sample.csv — small sample Statcast pull so the notebook runs out of the box
src/chase_dollander_src.py — standalone copy of the notebook's plotting/analysis functions, for reuse elsewhere

## What the notebook does
* Data cleaning — prepares the Statcast pull and tags each pitch as thrown at Coors or elsewhere
* Barrel Rate by Count — barrel rate broken out by ball-strike count
* Barrel Rate by Pitch — barrel rate broken out by pitch type
* What's Going on with the Cutter? — a closer look at the cutter specifically, motivated by its home/road gap
* Slugging by Pitch Location — xSLG heat map over the strike zone (by zone and raw plate coordinates) for balls in play
* Whiffs by Pitch Location — whiff-rate heat map over the strike zone, same zone-based layout
* Simple Stats by Pitch Type — pitch-level summary stats
* Home/Road Splits — batting average, OBP, and slugging against, home vs. road
* Euclidean Movement Delta — distance between a pitch's average movement (pfx_x/pfx_z) at Coors vs. elsewhere, per pitch type
* Pitch-Specific Home/Road Metrics — Savant-style BA/xBA/SLG/xSLG by pitch type, home vs. road

## Running it
1. Install dependencies: pandas, numpy, matplotlib, pybaseball.
2. Open notebook/chase_dollander_analysis.ipynb and run top to bottom.
3. Check the data-loading cell's path against sample_data/savant_through_2025_sample.csv before running — same issue as your other two repos, this one may
still point at a Colab/Drive path that doesn't exist locally.

## Data
Pitch-level Statcast data via pybaseball / Baseball Savant.
