# Insights from new OSM editors at a province level

Highlights

📊 Analyzing Q1 2026 new OSM editors in Andhra Pradesh, India reveals critical onboarding patterns.

✨ Only 32% of a newcomer's very first edits are completely free of technical errors.

⚠️ Low-severity issues (like abbreviation errors or duplicate node-way geometries) impact 49% of changesets.

📉 Retention is critically low: under 3% of new mapping accounts continue editing after receiving feedback.

💡 Localized, faster community validation workflows are essential to support and retain mapping talent.




![OSM newbie editor changesets quality (severity) distribution in Q1 2026 for Andhra Pradesh, India](https://upload.wikimedia.org/wikipedia/commons/thumb/8/81/OSM-Newbie-severity-AP-India-Q1-2026.png/330px-OSM-Newbie-severity-AP-India-Q1-2026.png)
*OSM newbie editor changesets quality (severity) distribution in Q1 2026 for Andhra Pradesh, India*

About 450 editors join [OpenStreetMap](https://wiki.openstreetmap.org/wiki/About_OpenStreetMap) and contribute their first edit everyday based on a study for the year 2023.[^1] Despite diverse OSM  review tools and processes, there were few studies about OSM new editor data quality at country level.[^2] Very little is known about their contribution quality and persistence  at province level. This need was identified in the first ever desk analysis of [State of the map for Andhra Pradesh in 2025](https://wiki.openstreetmap.org/wiki/Andhra_Pradesh/SotM). Even attempting to statistically analyze is not easy, given the need to query databases with specialized programs.  OSM Changeset Analyser([OSMCha](https://wiki.openstreetmap.org/wiki/OSMCha)) is a very good tool for reviews. Using OSMCha and OSM APIs, I built a small Python Jupyter notebook program with help from Github Copilot.  I applied this to understand the new editors contributions for [Andhra Pradesh](https://wiki.openstreetmap.org/wiki/Andhra_Pradesh) province of [India](https://wiki.openstreetmap.org/wiki/India) for Q1, 2026. I found that 32% of first edit changesets are of good quality. 49%  have low severity issues. Only 3% continue the edit  activity in the subsequent 30 days after discussion on their first changesets. This program can be reused easily by  modifying OSMCHA's AOI filter identifier and OSMCHA user token.

## Review process using OSMCha
![A screenshot of review of a changeset in OSMCha](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b2/OSMCha_changeset_discussion.png/330px-OSMCha_changeset_discussion.png)
*A screenshot of review of a changeset in OSMCha*

A reviewer logs into OSMCha using their OSM credentials to generate an API authorization token. To isolate a new editor's very first contribution, an Area of Interest (AOI) or filter is configured using the metadata parameter `changesets_count__max=1`. An example filter for "Andhra Pradesh" province is given as [example](https://osmcha.org/filters?aoi=7a484822-628c-4d23-b41a-8d2a1a76f0b7), which can be modified.

Reviewers can then perform three primary actions on a changeset:

1. **Flag:**Mark the changeset as "Good" or "Bad".
2. **Tag (for "Bad" changesets):** Apply qualitative assessment tags regarding Severity (Low, High, Critical), Resolution, and Intentionality, or flag it for the Data Working Group (DWG).
3. **Discuss:** Add a discussion message with constructive feedback. **Note: This is the only step that triggers an on-site notification and email to the new editor via OSM**.

New editor  may respond with further edits or may ignore the review.

Same reviewer or another reviewer can update review tags later based on feedback from the editor or after further edits.

## Case study
![Location of centre of changeset bounding box of newbie edits](https://upload.wikimedia.org/wikipedia/commons/thumb/7/76/OSM-Newbie-changeset-locations-AP-India-Q1-2026.png/330px-OSM-Newbie-changeset-locations-AP-India-Q1-2026.png)
*Location of centre of changeset bounding box of newbie edits*

I have been reviewing new editors' first changeset contributions for more than 9 months regularly starting from Q4,2025 for the province of Andhra Pradesh in India. There are no other reviewers participating in this task.   I was curious to understand whether my effort is making any difference, as only two new editors reached out to me over OSM email. 

I created a [new filter (link temporary: pickup aoi id from the url and use it in software)](https://osmcha.org/filters?aoi=05ef4393-c799-4d3e-aec1-25c317d0c79d) for the specified duration with review status blank for the duration of study. Basic statistical analysis of new editors' first changeset in terms of quality  as reflected by severity, issue resolution  and also the activity following the first review discussion for thirty days was done. The [Python Jupyter notebook software](https://github.com/arjunaraoc/osm-newbie-stats) created for this work is available on Github.

### Month wise changsets 
The following table gives the number of  first changesets of new editors in the month of observation. Total number is 122, which means 14 new editors edit every 10 days

| Serial No | Year-Month | First Changesets |
| :--- | :--- | :--- |
| 1 | 2026-01 | 27 |
| 2 | 2026-02 | 60 |
| 3 | 2026-03 | 35 |

### Geographic distribution
I did analysis of district wise changeset distribution based on the center of the changset bounding box. 24 districts were covered by changesets. Guntur district had maximum coverage from 21 changesets followed by Krishna with 13. Annamayya and Parvathipuram Manyam districts had 1 changeset each.  Guntur and Krishna had changesets of 5, 6 due to [Hot OSM Project 17520](https://tasks.hotosm.org/projects/17520), which was disaster mapping project launched in September 2024 to help Vijayawada flood relief efforts. After excluding these, Guntur (16),  Bapatla (9), Palnadu (8) are ranked top districts for changesets. Four districts namely Chittoor, Sri Sathya Sai, Alluri Sitharama Raju, Polavaram districts did not have changesets. One changeset center is in Telangana province near the border with Andhra Pradesh.

### Qualitative analysis from reviews
All 114 reviews were done by 'user:arjunaraoc'. Most of the new user changeset issues are related to the following:

1. **Tags:** Use of abbreviations like Rd for 'Road', all upper case  text or non standard tags,  Violation of OSM policies like Personally identifiable information.
2. **Feature geometry:** Creating both a way and a node to represent the same feature.
3. **Number of edited features:** Some times a new editor creates a changeset with too many feature edits like several road changes or addition of several buildings. As there are bound to be  mistakes, such changesets are likely to be reverted. It is better for new users to make few edits 1-5 for a similar feature as it helps the reviewer also in giving useful feedback.
4. **Comments:** Unclear comments
5. **Source:** No mention of local knowledge as source when the imagery used as source does not reflect the edit

### Changeset comments analysis
![Word cloud of top 10 words from 122 changeset comments of new users of OSM](https://upload.wikimedia.org/wikipedia/commons/thumb/8/8a/OSM-Newbie-comments-wordcloud-AP-India-Q1-2026.png/330px-OSM-Newbie-comments-wordcloud-AP-India-Q1-2026.png)
*Word cloud of top 10 words from 122 changeset comments of new users of OSM*

Top 10 words used in editor comments with their frequencies are given below

| Word | Count |
| :--- | :--- |
| created | 35 |
| road | 26 |
| added | 21 |
| near | 14 |
| hotosmproject17520 | 11 |
| osmindia | 11 |
| andhramapping24 | 11 |
| updated | 11 |
| residential | 8 |
| highways | 8 |

From the table, it can be seen that 'Road' seems to be the most edited feature. 
It is observed that 13 out of 122 (about 11%) contributed only one point.

The median counts of features created, modified, delete per changeset are 5.5, 1.0, and 0.0 respectively.

### Time taken for assessment/discussion
Editors can flag their changeset for review requests while submitting the changeset. Out of the total 122 changesets, 39 (32%) were requested for review. None of HOT OSM Project contributors requested a review. Irrespective of the review request flag, 114 were assessed. Out of 8 that were unassessed, 7 were for Hot OSM Project 17520.  113 were discussed. The average time taken for discussion was 14 days, with a minimum of 4 days  and maximum of 60 days.

### Severity analysis
![OSMCha showing sample review of changesets for Andhra Pradesh, India](https://upload.wikimedia.org/wikipedia/commons/thumb/c/ce/OSMCha_reviewed_filter_for_AP.png/330px-OSMCha_reviewed_filter_for_AP.png)
*OSMCha showing sample review of changesets for Andhra Pradesh, India*

![OSM newbie editor changesets quality (severity) distribution](https://upload.wikimedia.org/wikipedia/commons/thumb/8/81/OSM-Newbie-severity-AP-India-Q1-2026.png/330px-OSM-Newbie-severity-AP-India-Q1-2026.png)
*OSM newbie editor changesets quality (severity) distribution*

A flow diagram which categorizes the changesets  based on severity when a changeset was assessed 'Bad' is shown. Severity rating has three options 'low', 'high', and 'critical'. Out of 122 total changesets, 114  were checked. 39 were found to be good and 75 bad.  Low severity was assigned for 59 and high severity for  10.  None were assigned critical severity. There was no rating for 6 changesets.

### Issue resolution analysis
![OSM newbie editor changesets issue resolution distribution](https://upload.wikimedia.org/wikipedia/commons/thumb/6/62/OSM-Newbie-resolution-AP-India-Q1-2026.png/330px-OSM-Newbie-resolution-AP-India-Q1-2026.png)
*OSM newbie editor changesets issue resolution distribution*

A flow diagram which categorizes the changesets  based on issue resolution when a changeset was assessed 'Bad' is shown. Issue resolution rating has two options 'Resolved', 'Unresolved'. Out of 122 total changesets, 114  were checked. 39 were found to be good and 75 bad.  'Resolved' was assigned for 59 and 'Unresolved' for  13. Resolution status was not availble for 3 changesets.

### Newbie edit activity after discussion
![Newbie editor changeset count within 30 days after discussion on first changeset](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2c/OSM-Newbie-edits-after-discussion-AP-India-Q1-2026.png/330px-OSM-Newbie-edits-after-discussion-AP-India-Q1-2026.png)
*Newbie editor changeset count within 30 days after discussion on first changeset*

113 changesets out of 122 were discussed via OSMCha. The editor activity was checked for 30 days after the discussion and number of editors per changesets of 0 to 8, 9+ were plotted.  It is observed that 102 editors did not make any further edits. 1 or more edits were made by 11 editors. Only 3 editors made 9+ edits. A long duration study with 1000 changesets or more is needed to understand the percentage of editors who become active editors. It could be compared with newbie editors persistence for a month when they do not receive review feedback.

## Lessons learnt
1. **Reduce time taken for review:** The review delay for about 11 cases extended beyond a month. It is desirable to review the first changesets in 1-2 weeks. Using RSS feed from OSMCha can help in noticing the new edits faster. More reviewers can also help as 32% of changesets have "Request review" enabled.
2. **Enable the new editor to fix issues with low severity:** While reviewing, minor mistakes were fixed and the same was informed to the editor via discussion comment. Changeset resolution was set to 'Resolved'. As suggested in [OSMCha review tips](https://wiki.openstreetmap.org/wiki/Welcome_tool/OSMCha#To_Fix_or_Not_to_Fix), it is better to give suggestions for low severity issues through discussion, to encourage the editor to make required changes.
3. **Explain rating bad is required even for minor mistakes due to software limitation:** Another suggestion that I missed is to explain the limitation in assigning good/bad for a changeset in discussion comment, to not discourage new editors when then see a review marked as bad.

## Conclusion and Further work
The analysis of OSM new editors' first changesets showed that 32% of first changesets are of good quality. 49% changesets have low severity issues. Only 3% of new editors continue the edit  activity after discussion on their first changesets.

Repeating the study  in future for a longer period with a larger count of changesets can help improve the accuracy of statistics. Using Ohsome Now API, the number of features, the types of features  edited can also be analyzed for active new editors to nurture them.

## Acknowledgements
Github Co pilot was very helpful in coming up with the initial version of software program from a simple chat prompt. The draft of this article was updated manually based on useful review feedback from Gemini AI. It also helped in converting the wiki code draft to kramdown format of OSM User diary.

## References
[^1]: [Analyzing the Changesets of OSM Newcomers](https://heigit.org/analyzing-the-changesets-of-osm-newcomers/), Heigit, 29 January 2024.

[^2]: Toshikaju Seto, Hiroshi Kanasugi, Yuichiro Nashimura, [Quality Verification of Volunteered Geographic Information Using OSM Notes Data in a Global Context (2.Related work)](https://www.mdpi.com/2220-9964/9/6/372)", *ISPRS Int. J. Geo-Inf.*, 6 June 2020.
