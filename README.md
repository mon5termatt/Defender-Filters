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

this command bans any user that posts nitro or steam scams
##### big thanks to Naeng#0001

```
name: antiscam
rank: 2
event: on-message
if:
  - if-any:
     - message-matches-any: ["*steamconm*", "*stearncor*", "*steamncon*", "*steamcommi*", "*steamcomun*", "*steamcommun*", "*steamcomminut*"]
     - message-matches-any: ["*steamcommunytu*", "*steamcommunityu*", "*steancommunytiu*", "*stearncomminuty*"]
     - message-matches-any: ["*d1scord*", "*dlscord*", "*discorb*", "*discorcl*", "*discords-*", "*d1scord-*", "*discordgift*", "*d1scord-gift*", "*dlscord-gift*"]
     - message-matches-any: ["*discordgift*", "*d1scord-gifts*", "*dlscord-gifts*", "*d1scord-claim*", "*dlscord-claim*", "*d1scord-airdrop*", "*dlscord-airdrop*"]
     - message-matches-any: ["*d1scord-nitro*", "*dlscord-nitro*", "*nitrogift*", "*discord*wales*", "*givenitro*", "*free-nitro*", "*roblox-com*"]
     - message-matches-any: ["*?pantner*", "*give-nitro*", "*com/gift*", "*info/promo*", "*trade/offer*", "*giveaway/discord*", "*&token*", "*/airdrop*"]
  - if-not:
     - is-staff: true
do:
  - ban-user-and-delete: 1
  - send-mod-log: "User banned for linking a malicious URL." 
  - notify-staff:
      title: "Malicious Link"
      content: "$user_mention has sent a malicious link in $channel_mention - `$message_clean`"
      jump_to_ctx_message: true
      qa_target: $user_id # Quick action target
      qa_reason: "Phishing Link/Token Grabber" # Quick action reason, optional
      no_repeat_for: 30 seconds # Ensures that this notif. won't be sent again in the next 30 secs
      no_repeat_key: $rule_name-1 # An unique key that identifies this notif., make sure to set this too
  - send-message: [$channel_id, "Malicious Link was detected and removed (User may of been token logged)"]
  - delete-last-message-sent-after: 60 seconds
```

### dotru

this command will delete any blacklisted domain and warn the user

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

This Command will mute anyone who doesnt have the staff role defined by defender, use with caution.

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
  - add-user-heatpoint: 1h
  - notify-staff:
    title: "Warning!"
    content: "$user_mention Posted `$message_clean.` The Message Was Deleted."
    jump_to_ctx_message: true
    qa_target: $user_id # Quick action target
    qa_reason: "Spamming messages" # Quick action reason, optional
    no_repeat_for: 30 seconds # Ensures that this notif. won't be sent again in the next 30 secs
    no_repeat_key: $rule_name-1 # An unique key that identifies this notif., make sure to set this too 
  - send-message: [$channel_id, "$user_mention | Please do not attempt to ping everyone."]
  - delete-last-message-sent-after: 60 seconds
```

### shortener

#### wip
this one tries to prevent link shorteners. I havent fully made the list yet. some of these dont work.

```
name: shortener 
rank: 2
priority: 1
event: on-message
if:
  - message-matches-any: ["*bit.ly*", "*rb.gy*", "*short.io*", "*linklyhq.com*", "*clickmeter.com*", "*pixelme.me*", "*bl.ink*", "*cutt.ly*", "*soo.gd*", "*tinycc.com*", "*clkim.com*", "*tinyurl.com*", "*t2mio.com*", "*tiny.ie*", "*shorturl.at*", "*bit.do*", "*yourls.org*", "*musicjet.com*", "*adf.ly*", "*is.gd*"]
do:
  - delete-user-message:
  - add-user-heatpoint: 1h
    - notify-staff:
      title: "Warning!"
      content: "$user_mention Posted `$message_clean.` The Message Was Deleted."
      jump_to_ctx_message: true
      qa_target: $user_id # Quick action target
      qa_reason: "Spamming messages" # Quick action reason, optional
      no_repeat_for: 30 seconds # Ensures that this notif. won't be sent again in the next 30 secs
      no_repeat_key: $rule_name-1 # An unique key that identifies this notif., make sure to set this too 
  - send-message: [$channel_id, $user_mention | Please Refrain From Using Link Shorteners.]
  - delete-last-message-sent-after: 60 seconds
```

### deleteall

dont add this one, this one is a joke

```
name: deleteall
rank: 2
event: on-message
if:
  - message-matches-any: ["*"]
do:
  - delete-user-message:
```

### 
```

```
