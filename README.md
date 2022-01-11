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
priority: 1
event: on-message
if:
  - if-any:
     - message-matches-any: ["*steamconm*", "*stearncor*", "*steamncon*", "*steamcommi*", "*steamcomun*", "*steamcomminut*"]
     - message-matches-any: ["*steamcommunytu*", "*steamcommunityu*", "*steancommunytiu*", "*stearncomminuty*"]
     - message-matches-any: ["*d1scord*", "*dlscord*", "*discorb*", "*discojd*", "*discopd*", "*discorcl*", "*discoord*", "*discords*"]
     - message-matches-any: ["*discsrd*", "*steamdiscord*", "*discrode*", "*dlsccord*", "*discordg*"]
     - message-matches-any: ["*gg.gg*", "*discord-nitro*"]
     - message-matches-any: ["*nitrogift*", "*discord*wales*", "*givenitro*", "*free-nitro*", "*roblox-com*"]
     - message-matches-any: ["*?pantner*", "*give-nitro*", "*com/gift*", "*info/promo*", "*trade/offer*", "*giveaway/discord*", "*&token*", "*/airdrop*"]
  - if-not:
     - is-staff: true
do:
  - send-message: [$user_id, "You have been banned from $guild for attempting to scam users. (You can Submit a ban appeal here: https://xxxxxxxxxxxxxxxxxxxxxx.com)"]
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
     - is-helper: true
do:
  - delete-user-message:
  - send-message: [$user_id, "You have been muted in $guild for attempting to ping everyone. Please wait for a moderator to review your message."]
  - send-message: [$user_id, "If it is found to be a scam then you will be banned. (You can Submit a ban appeal here: https://xxxxxxxxxxxxxxxxxxxxxx.com)"]
  - punish-user:
  - send-mod-log: "User Muted for attempting to ping everyone." 
  - notify-staff:
      title: "Attempted Ping"
      content: "$user_mention tried to ping everyone in $channel_mention - `$message_clean`"
      thumbnail: $user_avatar_url
      footer_text: "They Done Fucked Up"
      ping: true
      jump_to_ctx_message: true
      qa_target: $user_id # Quick action target
      qa_reason: "Attempted Everyone Ping" # Quick action reason, optional
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
priority: 2
event: on-message
if:
- if-any:
  - message-matches-any: ["*linklyhq.com*", "*clickmeter.com*", "*pixelme.me*", "*bl.ink*", "*tinycc.com*"]
  - message-matches-any: ["*clkim.com*", "*tinyurl.com*", "*t2mio.com*", "*tiny.ie*", "*shorturl.at*"]
  - message-matches-any: ["*bit.do*", "*yourls.org*"]
  - message-matches-any: ["*.ru/*", "*.link/*", "*.su/*", "*.ly/*", "*.gy/*", "*.gd/*", "*.io/*"]
- if-not:
     - is-staff: true
     - message-matches-any: ["*plati.ru*"]
do:
  - send-mod-log: "Message Removed Due to Link Shortener or Blacklisted Link."  
  - delete-user-message:
  - add-user-heatpoint: 1h
  - notify-staff:
      title: "Blacklisted Link"
      content: "$user_mention has sent a blacklisted link in $channel_mention - `$message_clean`"
      jump_to_ctx_message: true
      qa_target: $user_id # Quick action target
      qa_reason: "Blacklisted Link" # Quick action reason, optional
      no_repeat_for: 30 seconds # Ensures that this notif. won't be sent again in the next 30 secs
      no_repeat_key: $rule_name-1 # An unique key that identifies this notif., make sure to set this too  
  - send-message: [$channel_id, $user_mention | It appears you posted a blacklisted link. If you feel like this was in error then submit a request here. <https://XXXXXXXXX.com>]
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
