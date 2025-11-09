# Gaming Data - Sample Datasets with User Journeys

This package contains **realistic gaming-focused sample datasets** designed for Mixpanel Warehouse Connectors, featuring **consistent user journeys** that track complete player progression through games.

## 🎮 Dataset Overview

| Dataset | Rows | File Size | Description |
|---------|------|-----------|-------------|
| **Events** | 124,006 | ~32 MB | Complete player journeys with 100+ gaming event types |
| **User Profiles** | 5,000 | ~1.1 MB | Player profiles with gaming-specific attributes |
| **Group Profiles** | 200 | ~44 KB | Gaming studio/publisher profiles |
| **Lookup Table** | 1,000 | ~132 KB | In-game items, weapons, armor, and collectibles |
| **Total** | **130,206** | **~33 MB** | Complete gaming analytics package |

### Key Feature: User Journey Consistency

**Every player has a complete, realistic journey:**
- **Average 24.8 events per user** (range: 4-50 events)
- **Chronological progression** from account creation through gameplay
- **Natural event sequences** (e.g., Game Started → Level Started → Level Completed → Loot Collected)
- **State tracking** (player level, currency balance, achievements progress)
- **Session-based gameplay** with realistic time gaps between sessions

---

## 🎯 Gaming Event Types (100+ Events)

### Onboarding & Account (9 events)
- Account Created, Tutorial Started/Completed, First Login, Daily Login
- Profile Customized, Avatar Changed, Username Changed, Settings Updated

### Core Gameplay (20 events)
- Game Started/Completed/Quit
- Level Started/Completed/Failed
- Mission Started/Completed/Failed
- Quest Accepted/Completed
- Challenge Started/Completed
- Boss Fight Started, Boss Defeated, Boss Fight Failed

### Character Progression (10 events)
- Character Created, Character Level Up, Character Class Changed
- Skill Unlocked/Upgraded, Ability Used
- Talent Tree Updated, Experience Gained, Rank Increased, Prestige Unlocked

### Items & Economy (16 events)
- Item Purchased/Sold/Equipped/Unequipped/Crafted/Upgraded/Enchanted
- Loot Collected, Chest Opened, Reward Claimed
- Currency Earned/Spent, Premium Currency Purchased
- Subscription Started/Renewed/Canceled

### Social & Multiplayer (19 events)
- Friend Added/Removed, Message Sent
- Guild Joined/Left/Created
- Team Formed, Matchmaking Started, Match Found/Started/Completed
- PvP Battle Started, PvP Victory/Defeat
- Co-op Mission Started/Completed
- Trade Initiated/Completed, Gift Sent/Received

### Engagement & Retention (14 events)
- Daily Reward Claimed, Weekly Challenge Completed, Monthly Event Participated
- Season Pass Purchased, Battle Pass Level Up
- Achievement Unlocked, Leaderboard Viewed
- Tournament Joined/Won
- Stream Started/Ended, Replay Watched, Screenshot Taken, Video Shared

### Monetization (10 events)
- Store Visited, Bundle Viewed, Special Offer Viewed
- IAP Initiated/Completed/Failed
- Ad Watched, Rewarded Ad Completed
- Offer Wall Viewed, Cross Promotion Clicked

### Technical & Support (10 events)
- Game Crashed, Bug Reported, Feedback Submitted
- Support Ticket Created/Resolved
- Game Updated, DLC Purchased/Installed
- Mod Installed, Settings Changed

---

## 📊 Events Dataset Schema

### Core Event Fields

| Column | Type | Example | Description |
|--------|------|---------|-------------|
| `event_name` | String | "Level Completed" | Name of the gaming event |
| `timestamp` | Timestamp | "2024-08-15 14:23:45" | When the event occurred |
| `user_id` | Integer | 1234 | Player identifier |
| `device_id` | String | "device_1234_567890" | Device identifier |
| `session_id` | String | "session_1234_5678" | Gaming session identifier |
| `platform` | String | "PC" | PC, PlayStation, Xbox, Nintendo Switch, Mobile iOS/Android, Steam Deck |
| `game_title` | String | "Legends of Azeroth" | Name of the game |
| `game_version` | String | "2.15.43" | Game version number |
| `player_level` | Integer | 42 | Current player level |
| `currency_balance` | Integer | 15000 | Soft currency balance |
| `premium_currency_balance` | Integer | 250 | Premium currency balance |
| `json_properties` | JSON | '{"fps": 60, "ping": 45}' | Technical metadata |
| `group_key` | Integer | 12 | Gaming studio/publisher ID |

### Event-Specific Properties

**Level Events** (Level Started/Completed/Failed):
- `level_number`, `level_difficulty`, `level_type`
- `completion_time_seconds`, `score`, `stars_earned` (for completed levels)

**Purchase Events** (Item Purchased, Premium Currency Purchased):
- `item_id`, `item_name`, `item_type`, `item_rarity`
- `price`, `currency_type`, `payment_method`

**Match/PvP Events** (Match Started/Completed, PvP Victory/Defeat):
- `match_id`, `match_type`, `team_size`, `map_name`
- `kills`, `deaths`, `assists`, `match_duration_seconds`

**Character Events** (Character Created/Level Up):
- `character_class`, `character_name`
- `new_level`, `experience_gained`

**Achievement Events**:
- `achievement_id`, `achievement_name`, `achievement_rarity`, `achievement_points`

**Guild/Team Events**:
- `guild_id`, `guild_name`, `guild_level`, `guild_member_count`

---

## 👤 User Profiles Dataset Schema

### Player Identity & Account

| Column | Type | Description |
|--------|------|-------------|
| `user_id` | Integer | Unique player identifier (PRIMARY KEY) |
| `username` | String | Gaming username (e.g., "ShadowHunter42") |
| `email` | String | Player's email address |
| `subscription_tier` | String | Free, Bronze, Silver, Gold, Platinum, Diamond |
| `account_created_date` | Date | When account was created |
| `last_login_date` | Date | Most recent login |

### Demographics & Preferences

| Column | Type | Description |
|--------|------|-------------|
| `country` | String | Player's country |
| `region` | String | Geographic region |
| `preferred_platform` | String | Favorite gaming platform |
| `preferred_genre` | String | Favorite game genre |
| `language` | String | Preferred language |
| `age_group` | String | Age bracket (13-17, 18-24, 25-34, 35-44, 45+) |

### Gaming Stats & Progress

| Column | Type | Description |
|--------|------|-------------|
| `is_active` | Boolean | Currently active player |
| `total_playtime_hours` | Integer | Total hours played |
| `player_level` | Integer | Overall player level (1-100) |
| `total_achievements` | Integer | Achievements unlocked |
| `games_owned` | Integer | Number of games owned |
| `win_rate` | Float | Overall win rate (0-1) |
| `kd_ratio` | Float | Kill/Death ratio |
| `favorite_character_class` | String | Preferred character class |

### Social & Economy

| Column | Type | Description |
|--------|------|-------------|
| `friends_count` | Integer | Number of friends |
| `guild_member` | Boolean | Member of a guild |
| `lifetime_spend` | Float | Total money spent (USD) |
| `premium_currency_balance` | Integer | Current premium currency |
| `soft_currency_balance` | Integer | Current soft currency |

### Acquisition & Security

| Column | Type | Description |
|--------|------|-------------|
| `referral_source` | String | How player was acquired |
| `email_verified` | Boolean | Email verification status |
| `two_factor_enabled` | Boolean | 2FA enabled |
| `marketing_opt_in` | Boolean | Marketing preferences |

---

## 🏢 Group Profiles Dataset Schema

Gaming studios and publishers for B2B analytics.

| Column | Type | Description |
|--------|------|-------------|
| `group_key` | Integer | Unique studio identifier (PRIMARY KEY) |
| `studio_name` | String | Studio/publisher name |
| `domain` | String | Company domain |
| `studio_type` | String | Indie, AA Studio, AAA Studio, Publisher, Mobile Developer |
| `founded_date` | Date | When studio was founded |
| `country` | String | Studio headquarters country |
| `region` | String | Geographic region |
| `employee_count` | Integer | Number of employees |
| `games_published` | Integer | Total games published |
| `active_games` | Integer | Currently active games |
| `total_players` | Integer | Total registered players |
| `monthly_active_users` | Integer | MAU across all games |
| `annual_revenue` | Integer | Annual revenue in USD |
| `primary_platform` | String | Main platform focus |
| `primary_genre` | String | Main genre focus |
| `has_live_service` | Boolean | Operates live service games |
| `has_esports_team` | Boolean | Has esports presence |
| `community_size` | Integer | Total community members |
| `discord_members` | Integer | Discord server members |
| `twitch_followers` | Integer | Twitch followers |
| `youtube_subscribers` | Integer | YouTube subscribers |
| `metacritic_average` | Float | Average Metacritic score |
| `steam_rating` | String | Steam review rating |
| `awards_won` | Integer | Industry awards won |
| `partnership_tier` | String | Partnership level |
| `support_response_time` | String | Average support response time |

---

## 🎁 Lookup Table Dataset Schema

In-game items, weapons, armor, and collectibles.

| Column | Type | Description |
|--------|------|-------------|
| `id` | Integer | Unique item identifier (PRIMARY KEY) |
| `item_name` | String | Item name (e.g., "Legendary Sword of Power") |
| `item_type` | String | Weapon, Armor, Helmet, Shield, Boots, Gloves, Ring, Amulet, Potion, etc. |
| `rarity` | String | Common, Uncommon, Rare, Epic, Legendary, Mythic |
| `level_requirement` | Integer | Minimum player level required |
| `price_soft_currency` | Integer | Price in soft currency |
| `price_premium_currency` | Integer | Price in premium currency |
| `price_usd` | Float | Real money price |
| `attack_power` | Integer | Attack stat bonus |
| `defense_power` | Integer | Defense stat bonus |
| `magic_power` | Integer | Magic stat bonus |
| `health_bonus` | Integer | Health points bonus |
| `mana_bonus` | Integer | Mana points bonus |
| `speed_bonus` | Integer | Speed stat bonus |
| `critical_chance` | Float | Critical hit chance (0-1) |
| `durability` | Integer | Item durability |
| `is_tradeable` | Boolean | Can be traded with other players |
| `is_craftable` | Boolean | Can be crafted |
| `is_enchantable` | Boolean | Can be enchanted |
| `drop_rate` | Float | Drop rate probability |
| `character_class_restriction` | String | Class restriction (if any) |
| `release_date` | Date | When item was added to game |
| `is_seasonal` | Boolean | Seasonal exclusive |
| `is_event_exclusive` | Boolean | Event exclusive |

---

## 🎮 Sample User Journey

Here's an example of a complete player journey showing natural progression:

```
User ID: 1 (33 total events)

1. 2025-03-07 00:00:00 - Account Created (Level: 1)
2. 2025-03-07 00:05:00 - Tutorial Started (Level: 1)
3. 2025-03-07 00:11:00 - Tutorial Completed (Level: 1)
4. 2025-03-07 00:37:00 - Loot Collected (Level: 1)
5. 2025-03-07 00:52:00 - Quest Accepted (Level: 1)
6. 2025-03-07 01:06:00 - Settings Changed (Level: 1)
   [14 hour gap - player offline]
7. 2025-03-07 15:06:00 - Daily Login (Level: 1)
8. 2025-03-07 15:18:00 - Daily Login (Level: 1)
9. 2025-03-07 16:18:00 - PvP Battle Started (Level: 1)
10. 2025-03-07 16:40:00 - Daily Reward Claimed (Level: 1)
    [36 hour gap - new session]
11. 2025-03-09 04:07:00 - Game Started (Level: 1)
12. 2025-03-09 04:14:00 - Level Completed (Level: 1)
    ... continues with natural progression
```

**Key Journey Features:**
- ✅ Starts with Account Created
- ✅ Tutorial flow (Started → Completed)
- ✅ Natural time gaps between sessions
- ✅ Progressive gameplay (quests, levels, battles)
- ✅ Engagement mechanics (daily logins, rewards)
- ✅ Consistent player state tracking

---

## 📈 Data Characteristics

### Realistic Gaming Patterns

1. **User Journey Consistency**: Every player has 4-50 events showing complete progression
2. **Temporal Realism**: Events span player's lifetime from account creation to present
3. **Session-Based Play**: Natural time gaps between gaming sessions (hours to days)
4. **Event Sequencing**: Logical event flows (e.g., Game Started before Level Started)
5. **State Progression**: Player level, currency, and achievements increase over time
6. **Platform Diversity**: 7 gaming platforms represented
7. **Genre Variety**: 15 game genres across 50+ game titles
8. **Global Player Base**: 15 countries, 6 regions
9. **Monetization Mix**: Free and paying players with realistic spending patterns
10. **Social Engagement**: Guild membership, friend counts, multiplayer events

### Distribution Statistics

- **Active Players**: 75% (3,750 users)
- **Guild Members**: ~50% of players
- **Average Events per User**: 24.8 events
- **Event Range**: 4-50 events per user
- **Total Events**: 124,006 events
- **Time Span**: Up to 2 years of player history

---

## 💡 Usage Examples

### Analyze Player Retention

```sql
SELECT 
  DATE(account_created_date) as cohort_date,
  COUNT(DISTINCT user_id) as players,
  AVG(total_playtime_hours) as avg_playtime,
  SUM(CASE WHEN is_active THEN 1 ELSE 0 END) * 100.0 / COUNT(*) as retention_rate
FROM user_profiles
GROUP BY cohort_date
ORDER BY cohort_date DESC;
```

### Track User Journey Funnel

```sql
WITH user_events AS (
  SELECT 
    user_id,
    MAX(CASE WHEN event_name = 'Account Created' THEN 1 ELSE 0 END) as created,
    MAX(CASE WHEN event_name = 'Tutorial Completed' THEN 1 ELSE 0 END) as tutorial,
    MAX(CASE WHEN event_name = 'Level Completed' THEN 1 ELSE 0 END) as first_level,
    MAX(CASE WHEN event_name LIKE '%Purchase%' THEN 1 ELSE 0 END) as purchased
  FROM events
  GROUP BY user_id
)
SELECT 
  SUM(created) as accounts_created,
  SUM(tutorial) as completed_tutorial,
  SUM(first_level) as completed_first_level,
  SUM(purchased) as made_purchase
FROM user_events;
```

### Monetization Analysis

```sql
SELECT 
  u.subscription_tier,
  COUNT(DISTINCT u.user_id) as players,
  AVG(u.lifetime_spend) as avg_ltv,
  COUNT(DISTINCT e.event_name) as unique_events,
  AVG(u.total_playtime_hours) as avg_playtime
FROM user_profiles u
LEFT JOIN events e ON u.user_id = e.user_id
WHERE e.event_name LIKE '%Purchase%'
GROUP BY u.subscription_tier
ORDER BY avg_ltv DESC;
```

### Item Popularity

```sql
SELECT 
  l.item_name,
  l.item_type,
  l.rarity,
  COUNT(*) as purchase_count,
  AVG(l.price_usd) as avg_price
FROM events e
JOIN lookup_table l ON e.item_id = l.id
WHERE e.event_name = 'Item Purchased'
GROUP BY l.item_name, l.item_type, l.rarity
ORDER BY purchase_count DESC
LIMIT 20;
```

### Player Progression Timeline

```sql
SELECT 
  user_id,
  event_name,
  timestamp,
  player_level,
  currency_balance,
  game_title
FROM events
WHERE user_id = 1
ORDER BY timestamp;
```

---

## 🎯 Perfect For Testing

- ✅ **Mixpanel Warehouse Connectors** - All 4 table types (Events, User Profiles, Group Profiles, Lookup Tables)
- ✅ **User Journey Analysis** - Complete player progression tracking
- ✅ **Retention Analytics** - Cohort analysis and churn prediction
- ✅ **Monetization Optimization** - IAP and subscription analysis
- ✅ **Engagement Metrics** - DAU/MAU, session length, feature adoption
- ✅ **Social Features** - Guild analytics, friend networks, multiplayer metrics
- ✅ **Game Balance** - Level difficulty, progression pacing, economy tuning
- ✅ **Live Ops** - Event participation, seasonal content performance
- ✅ **Platform Comparison** - Cross-platform player behavior
- ✅ **Studio Analytics** - Publisher performance, game portfolio analysis

---

## 📦 File Formats

All files are CSV format with:
- **Delimiter**: Comma (`,`)
- **Encoding**: UTF-8
- **Header Row**: Yes
- **Date Format**: `YYYY-MM-DD`
- **Timestamp Format**: `YYYY-MM-DD HH:MM:SS`
- **Boolean Values**: `True` / `False`

---

## 🎮 Gaming Industry Focus

This dataset is specifically designed for **gaming analytics** with:

- **Realistic Gaming Events**: 100+ event types covering all aspects of modern games
- **Player Progression**: Level-ups, skill unlocks, achievement tracking
- **In-Game Economy**: Soft currency, premium currency, item purchases
- **Social Features**: Guilds, friends, multiplayer, trading
- **Monetization**: IAP, subscriptions, season passes, ads
- **Live Service**: Daily rewards, events, challenges, tournaments
- **Multiple Genres**: Action, RPG, Strategy, MOBA, Battle Royale, Sports, etc.
- **Cross-Platform**: PC, Console, Mobile gaming
- **B2B Analytics**: Gaming studio/publisher performance tracking

---

## 📊 Schema Compliance

✅ **Fully compliant** with some classical Insight tool like Mixpanel Connector requirements:

- **Events**: Required `event_name` and `timestamp`, optional `user_id`, `device_id`, `json_properties`
- **User Profiles**: Required `user_id` primary key with rich gaming attributes
- **Group Profiles**: Required `group_key` primary key for studio/publisher data
- **Lookup Table**: Required `id` primary key for item catalog enrichment

---

**Generated**: October 24, 2025  
**Total Rows**: 130,206  
**Total Size**: ~33 MB  
**Focus**: Gaming Industry with Complete User Journeys

🎮 **Ready for gaming analytics!**


