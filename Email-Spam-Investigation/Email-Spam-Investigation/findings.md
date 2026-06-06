# Investigation Findings

## Key Observations

### Email Frequency Analysis

Analysis of sendmail logs showed a consistent volume of email activity over multiple days.

### Time-Based Analysis

The following query was used:

```spl
index=sample sourcetype=sendmail
| eval minute=strftime(_time,"%M")
| stats count by minute
| sort minute
```

Results revealed significant peaks at:

- 00
- 05
- 10
- 15
- 20
- 25
- 30
- 35
- 40
- 45
- 50
- 55

This pattern suggests activity occurring on 5-minute boundaries.

### Recipient Analysis

Top recipients included:

- root
- spamme@splunkit.com
- splunk@localhost
- root@splunk3.splunkit.com
- mark@splunk.com
### Assessment

The observed pattern is consistent with automated processing or scheduled tasks rather than user-driven activity.
