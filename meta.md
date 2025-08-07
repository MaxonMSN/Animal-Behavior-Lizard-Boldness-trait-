The following text describes the data file as well as the column names in that file.  

# Provided data file

- behavior_data.csv
	- includes the scores from the aggression and boldness behavioral assays performed on sleepy lizards (Tiliqua rugosa) from 2010 through 2017. Also contains lizard sex, mass, and tick counts.
	- Columns are described below.

# Columns 

- Lizard: the unique individual to which the focal observation (the current row) refers. 
- year: the calendar year of the focal observation
- Date: date in MM/DD/YYYY on which the current behavioral trial was performed
- aggression: the lizard's aggression score. Ranked on a 1-11 scale. This scale is described in: Godfrey et al. 2012. Lovers and fighters in sleepy lizard land: where do aggressive males fit in a social network? Animal Behavior. 
  - See Table 1 in the paper.
- boldness: the lizard's banana boldness score. This score reflected a lizard's response to a banana (a preferred food item) in a perceived situation of risk. Due to slight methodological differences among years in how the banana boldness assay was ranked, we standardized this metric within year. For example, the boldness values for lizard 2408 in year 2010 were: ((observed boldness scores for 2408 in 2010) - mean(all observed boldness scores in 2010))/sd(all observed curiosity scores in 2010)
- Sex: lizard sex. 0 is Female and 1 is Male. NA individuals had indeterminate sex.
- avgmass: the lizard's average mass for a given season (thus, for a given lizard, average mass will be the same for all observations within a single season). Provided in grams.
  - "season" refers to our field season, usually August - December (the Australian spring), which is the main period of sleepy lizard activity
  - outside of those months, sleepy lizards are much less active and difficult to find
  - in all text below, season refers to this activity period within each calendar year
- trialnum: the trial number within season of the behavioral observation. Lizards typically received aggression and boldness assays three times per season. This trial number refers to these within season trials (a lizard's first, second, third, etc. trial within season).
- assayyear: for a given observation, this column indicates whether this was the lizard's first, second, third, etc year experiencing the behavioral assays. So if a lizard experienced behavioral, assays in 2014, 2015, and 2017, then the trialyear for the assays in those years would be, respectively,
1, 2, and 3.
- yrsinsite: for a given observation, this column indicates the number of years that a lizard was presumed to have been in the study site. So considering the previous example (a lizard experienced behavioral assays in 2014, 2015, and 2017), the lizard missed the 2016 assays. This likely occurred not because the lizard left the site and came back, but because it was not found that season, or it was found after the behavioral assays were performed. Thus, for this example, yrsinstudy would be, respectively, 1, 2, and 4.
- avgbothNymph_Larva: this column records accumulated average (larvae + nymph) tick counts. Throughout the season, we counted lizards' ticks roughly every two weeks, assessing the number of larval, nymph, and adult ticks. 
  - Because ticks were counted roughly every two weeks within a season, but we typically assessed behaviour only three times per season, we had more tick counts per lizard than behavioural observations
  - For a given focal lizard, behavioural observations always occurred on a date where ticks were also assessed
  - We therefore determined a rolling average for the tick counts per behavioral trial per lizard
  - Specifically, to derive the accumulated tick average metric, we averaged a lizard's tick counts from the bi-weekly tick counts up to (inclusive) the current trial. 
    - If a lizard had two tick counts before its first behavioral trial and one tick count on the day of the first trial, the rolling average tick count for the first behavioral trial would average the tick counts from each of these three observations. 
    - For trial 2, tick counts from the start of the season through trial 2's date would be averaged, and so on for trial 3.
  - For this column, avgbothNymph_Larva, we used the sum of a lizard's larvae + nymphs within a count observation. 
- avgtotal: this column records accumulated average tick counts, as described above, but for all tick stages (larvae + nymph + adult). 

To better illustrate avgbothNymph_Larva and avgtotal, consider the following example table, which shows the tick counts (larvae/nymph/adult) at each counting event and whether behavioral trials also occurred at a given count.

|           | Tick Count 1 | Tick Count 2 | Tick Count 3 | Tick Count 4 |
| :-------- | :----------- | :----------- | :----------- | :----------- |
| BT trials | --           | Trial 1      | --           | Trial 2      |
| Ticks     | 10/1/2       | 5/0/2        | 1/1/0        | 10/2/0       |

In this table, behavioral trial 1 occurred the same day as the lizard's second tick count, and trial 2 occurred the same day
as the lizard's fourth tick count. In this situation, the tick scores would be:
- For Trial 1
  - avgbothNymph_Larva: [(10+1) + (5+0)] / 2
  - avgtotal: [(10+1+2) + (5+0+2)]/2
- For Trial 2
  - avgbothNymph_Larva: [(10+1) + (5+0) + (1+1) + (10+2)] / 4
  - avgtotal: [(10+1+2) + (5+0+2) + (1+1+0) + (10+2+0)]/4