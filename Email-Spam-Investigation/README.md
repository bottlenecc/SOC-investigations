# Email Spam Investigation

## Objective

Investigate email activity within sendmail logs using Splunk to determine whether the activity was malicious or automated.

## Environment

- SIEM: Splunk
- Data Source: Sample sendmail logs
- Sourcetype: sendmail

## Investigation Process

### 1. Review Email Activity

```spl
index=sample sourcetype=sendmail
```

### 2. Identify Top Recipients

```spl
index=sample sourcetype=sendmail
| top to
```

### 3. Analyze Email Volume Over Time

```spl
index=sample sourcetype=sendmail
| timechart span=1h count
```

### 4. Analyze Minute Distribution

```spl
index=sample sourcetype=sendmail
| eval minute=strftime(_time,"%M")
| stats count by minute
| sort minute
```

## Findings

- Email activity occurred continuously over multiple days.
- Significant activity was observed at 5-minute intervals.
- SpamAssassin flagged multiple messages as spam.
- Top recipients included root, spamme@splunkit.com, and localhost accounts.
- No major spikes or unusual surges were identified.

## Conclusion

The observed activity appears consistent with an automated process or scheduled task rather than a user-driven spam campaign. The recurring 5-minute pattern supports the hypothesis of automated mail processing.

## Skills Demonstrated

- Splunk SIEM
- Log Analysis
- Email Investigation
- Threat Hunting
- Event Correlation
- Security Monitoring
