# Defender-Filters
Redbot Defender Cog Filters


## Used with Redbot And Defender

#### Redbot: https://docs.discord.red/

#### Defender: https://github.com/Twentysix26/x26-Cogs

## How to Use

Step 1: Install Requirements above

Step 2: Run `[p] def warden upload`

Step 3: Upload the filters in `.txt` or `.yaml` format into the channel that you ran the above command

Step 4: When done, type Quit



### antiscam
```
name: antiscam
rank: 2
event: on-message
if:
  - if-any:
     - message-matches-any: ["*discord*wales*", "*nitrogift*", "*givenitro*", "*free-nitro*", "*discorcl*", "*discorb*", "*discrod*", "*roblox-com*"]
  - if-not:
     - is-staff: true
do:
  - ban-user-and-delete: 1
  - notify-staff: "$user_mention Posted ```$message_clean``` $user appears to be posting scams. he has been banned."
  - send-message: [$channel_id, "$user appears to be posting scams. he has been banned."]
  - delete-last-message-sent-after: 60 seconds
```
  
### tokenlog
```
name: tokenlog
rank: 2
event: on-message
if:
  - if-any:
     - message-matches-any: ["*steamcommunityu*", "*steancommunytiu*", "*stearncomminuty*", "*steamcommunytu*"]
     - message-matches-any: ["*?pantner*", "*trade/offer*", "*&token*"]
  - if-not:
     - is-staff: true
do:
  - ban-user-and-delete: 1
  - notify-staff: "$user_mention Posted ```$message_clean``` He appears to of been tokenlogged. he has been banned."
  - send-message: [$channel_id, "$user appears to of been tokenlogged. he has been banned."]
  - delete-last-message-sent-after: 60 seconds
```

### dotru
```
name: dotru
rank: 2
event: on-message
if:
  - if-any:
     - message-matches-any: ["*.ru*", "*.link*", "*.su*"]
  - if-not:
     - is-staff: true
     - message-matches-any: ["*plati.ru*"]

do:
  - delete-user-message:
  - notify-staff: $user_mention Posted ```$message_clean```
  - send-message: [$channel_id, $user_mention | Please Refrain From Posting Blacklisted Domains]
  - delete-last-message-sent-after: 60 seconds
```

### everyone
```
name: everyone
rank: 2
event: on-message
if:
  - if-any:
     - message-matches-any: ["*@everyone*"]
  - if-not:
     - is-staff: true
do:
  - delete-user-message:
  - punish-user:
  - notify-staff: "$user_mention Posted ```$message_clean``` As a Ping was attempted without the required roles he has been muted, check if this is a scam."
  - send-message: [$channel_id, "$user_mention | Please do not attempt to ping everyone."]
  - delete-last-message-sent-after: 60 seconds

```

### shortener
```
name: shortener
rank: 2
event: on-message
if:
  - message-matches-any: ["*bit.ly*", "*rb.gy*", "*short.io*", "*linklyhq.com*", "*clickmeter.com*", "*pixelme.me*", "*bl.ink*", "*cutt.ly*", "*soo.gd*", "*tinycc.com*", "*clkim.com*", "*tinyurl.com*", "*t2mio.com*", "*tiny.ie*", "*shorturl.at*", "*bit.do*", "*yourls.org*", "*musicjet.com*", "*adf.ly*", "*is.gd*"]
do:
  - delete-user-message:
  - notify-staff: "$user_mention Posted ```$message_clean.``` The Message Was Deleted."
  - send-message: [$channel_id, $user_mention | Please Refrain From Using Link Shorteners.]
  - delete-last-message-sent-after: 60 seconds
```

### 
```

```

### 
```

```
