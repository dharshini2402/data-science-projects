# GroupDNA — WhatsApp Group Behavioural Analytics

## Problem and objectives

WhatsApp chat exports combine conversations with system notices, media placeholders, deleted-message notices, and messages that wrap across multiple lines. GroupDNA parses those records and turns them into a readable summary of group activity, timing, vocabulary, response patterns, silent periods, and behavioural archetypes.

The project demonstrates Python fundamentals, file handling, dictionaries, functions, datetime calculations, and a NumPy activity matrix. The academic notebook follows the project brief's restrictions and keeps the analysis understandable and reproducible. A separate interactive dashboard presents the same calculated results.

## Dataset and findings

The default dataset, `hostel_bois_from_unlox_pdf.txt`, was reconstructed from the supplied 62-page `unlox.pdf`. Long messages wrapped across PDF lines are preserved as continuations. This is synthetic project data, not a private or real WhatsApp conversation.

The analysis found 3,178 timestamped entries from 1 April through 30 May 2024: 3,174 participant entries and 4 system entries. Participant activity includes 32 media entries and 15 deleted entries; 3,127 messages contain analyzable text. Participant totals match the brief's reference table:

| Participant | Entries |
| --- | ---: |
| Rahul | 953 |
| Priya | 718 |
| Neha | 635 |
| Aman | 490 |
| Karan | 354 |
| Vikas | 24 |

Rahul contributed the most messages. The busiest date was 4 May 2024 with 76 messages, and the busiest hour was 18:00–19:00 with 248 messages. After the notebook's stop-word filtering, `how` was the most frequent word, appearing 321 times. Rahul had the shortest average response gap at 34.9 minutes; Aman had the longest at 55.4 minutes. Vikas was silent on 44 of the 60 observed dates and had the longest continuous silent streak: 11 days, from 23 April to 3 May.

The PDF's illustrative target output gives different values for some metrics, including the busiest date/hour, word counts, and response times. This project reports calculations from the supplied chat rather than changing results to fit the illustration. The PDF says there are 3,177 total lines, while extraction produced 3,178 timestamped entries; this difference is documented and left unaltered.

## Features

1. **WhatsApp chat parser:** extracts timestamps, senders, and message text; handles system, media, deleted, blank, and multi-line entries.
2. **Group overview:** calculates total activity, participants, date range, duration, contribution percentages, word totals, and average text length.
3. **Most active day and hour:** reports daily and hourly activity peaks.
4. **NumPy activity heatmap:** builds a dynamic participant-by-24-hour matrix and prints a four-level text heatmap.
5. **Top words analysis:** counts filtered words for the group and each participant, with text-based frequency bars.
6. **Response speed and silent streaks:** measures reply gaps when the sender changes and finds consecutive inactive days.
7. **Personality archetypes:** scores all eight archetypes, assigns one exclusive primary label per participant, and includes the bonus Canteen Coordinator signal.
8. **Final GroupDNA report:** combines the calculated results into a screenshot-friendly terminal report.

The calculated primary archetypes are Rahul — The Spammer, Priya — The Group Mom, Aman — The Night Owl, Karan — The Storyteller, Neha — The Drama Queen, and Vikas — The Ghost. The bonus Canteen Coordinator counts campus food and tea terms relevant to Indian college life.

## Sample output

The preview below is rendered from the notebook's final report using the PDF-derived dataset.

![GroupDNA report preview](screenshots/groupdna_report_preview.png)

```text
GROUPDNA REPORT — Hostel Bois 4ever
60 days · 3,174 participant entries · 6 members
Busiest day: 2024-05-04 (76 messages)
Busiest hour: 18:00–19:00
Top filtered word: how (321)
Fastest average replier: Rahul (34.9 minutes)
Longest silent streak: Vikas (11 days)
```

## Conclusion

GroupDNA turns an irregular WhatsApp export into structured records and useful group-level summaries. The parser preserves participant activity while separating entries that cannot be analyzed as ordinary text. Python dictionaries support the counts and comparisons, datetime supports response and silence calculations, and NumPy stores hourly activity. The notebook and dashboard present results calculated from the supplied synthetic dataset, with differences from the brief's illustrative figures clearly identified.
