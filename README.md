# Web4 NFT Metadata Standard 🎸

by: [Douglas Butner](https://github.com/dougbutner) aka [Gudasol 🜛](https://ampl.ink/gudasol)

**The tl;dr:** Web4 incorporates geography and time as key primitives enabling futuristic algorithms. Using compatible attributes in your NFTs means your collections will be automatically compatible with [Web4](https://github.com/dougbutner/web-4).

> Web 4 catalyzes free will by empowering collective decision making to manifest common goals and desires. Web4 strives to create systems that are public, provable, and powerful. These systems find use in curation, community, and consensus. - from [The Web4 Manifesto](https://github.com/dougbutner/web-4)

# Watch an [Instructional Video](https://www.youtube.com/watch?v=GXjBQnV_Xm8) on creating your NFT via metadata standards

The Web4 NFT Standard is a future-positive standard used to create an [Atomic Assets schema](https://github.com/pinknetworkx/atomicassets-contract/wiki/Quickstart-Guide) to mint NFTs and make templates that are compatible with Web4 for any individual, collection, or application to create their own tokenized project.

## The benefits of using Time and Geography in your NFT are:
- [x] Curation by location
  - By putting up blinders to the rest of the world, Web4 helps people support local-first, so the best of the best can organically grow up the chain to the global stage.
- [x] Curation by time
  - By tracking when votes happen, more relevant displays can be built that not only catch trends but also create and magnify them. Instead of showing the total views a video has, a web4 app would show the views of the video for that day (or any other span of time).

## The standard can be extended to
- [x] Music NFTs
- [x] Art NFTs
- [x] Video NFTs
- [x] Photography NFTs
- [x] Tokenized Llama Farming
- [x] Other Collectibles
- [x] Anything you can think of

**There's no coding skills required.** You can apply the schema through the AtomicHub UI manually (easier, slower) or copy and paste it directly when calling the action. You can even [mint your NFT from your phone](https://www.youtube.com/watch?v=k0vt8v5iIn4).

This Schema exists within Atomic Asset's [NFT standard](https://github.com/pinknetworkx/atomicassets-contract) on the [atomicassets contract](https://wax.bloks.io/account/atomicassets).

Feel free to use or modify this schema for any purpose in accordance with the [license](LICENSE).



# Quick Summary 🗞️

This standard includes:

###  NFT Metadata
- Name
- Title
- About
- License
- Rarity

### IPFS media fields:

- img
- clip
- audio
- video
- backimg
- promo
- collectionimg

### Temporal fields:

- Timestamp
- Date
- Year
- Month
- Day

### Geographic fields:

- Location
- Nation
- State
- City
- Geotag





# Technical Summary ⚙️
All media fields use IPFS. This is stored as text. 

All other info fields are strings.

| Field name | Type | Description | 
| :--------: | :--: | :---------: |
| name       | string | NFT name as shown in marketplace |
| title      | string | The actual title of the work, use if different from name field |
| about      | string | Long Description of the NFT (Note you pay RAM for this, it isn't hashed) |
| img        | ipfs   | Primary image / Cover image shown in marketplace (if left blank, video will usually show) |
| clip       | ipfs   | Additional anything-goes IPFS hash |
| audio      | ipfs   | Audio file IPFS hash |
| video      | ipfs   | Primary Video file IPFS hash |
| backimg    | ipfs   | Back cover of album / single |
| promo      | ipfs   | Extra image or video for promo poster, QR code, etc |
| collectionimg | ipfs | Image that represents the collection, optional |
| timestamp  | string | Timestamp for the publication of the work (simplifies + supercedes date) |
| date       | string | Date when the work was published (supercedes / replaces Year/Month/Day) Recommended format is ISO 8601 "YYYY-MM-DD" because "MM-DD-YYYY" can be confused with "DD/MM/YYYY" but it's up to you. To cover all bases, set timestamp field as a backup |
| year       | string | Year when the work was published. Format: "YYYY". ⚠️ It's best to use either date or year/month/day, not both. |
| month      | string | Month when the work was published. Format: "MM" or English abbreviation (e.g., "Jan", "Feb", etc.) or full month name |
| day        | string | Day when the work was published. Format: "DD" or "D" |
| location   | string | Full location information in one field, format: "City, State, Nation" |
| nation     | string | Three-letter ISO country code (e.g., "USA", "BRA", "AUS", etc.) Please don't use anything else, as this is the easiest format for any application to integrate |
| state      | string | State or province for the location, format: Abbreviation convention used in nation (e.g., California as "CA", Antioquia as "ANT") |
| city       | string | City for the location, format: "City Name" |
| geotag     | string | GeoJSON Point stored as string, format "lat,lng" (e.g., "37.7749,-122.4194"), or a "[lat,lng]" coordinate array (e.g., "[37.7749, -122.4194]") |  
| credits    | string | Cridit collaborators, suggested format "Credit: Name, Credit Two: Name Two" |  
| license    | string | Declare license identifier for work on NFT, (Copyright, CC0, MIT, etc) |  
| rarity     | string | How scarce is this NFT? Abundant Common Uncommon Rare Epic Mythic Unique |  


# Caveats and Notes 📝
This standard has more time and geographic fields than any single collection should need, but that's okay.

🔑 Ensure you pick the best formats for geography and time for your needs AND future usability of third-parties. 

- Both the geographic and time fields have multiple routes, pick one and use it for the entire schema/collection 
  - Consider your use case carefully. Next consider future-proofness, and remember, all fields are optional.
- You should use either the date field or the year/month/day fields, not both. Timestamp is the most accurate, but it may not be easily understandable without decoding in a user interface
- Similarly, you should consider using `location` or `nation` & `state` & `city`, but may not need both. If using Location or Geotag as the primary geographic/geopolitical field, consider also including the three-letter country name, as it's very easy for apps to integrate.

# To use this Standard 

## The Easy Way

Use the user interface on Atomic Assets to:

1: [Create a Collection](https://wax.atomichub.io/creator)
2: Create a Schema by adding each field (replace your collection name in the URL): https://wax.atomichub.io/creator/collection/YOURCOLLECTIONNAME/create-schema
3: Select the new schema when making templates and minting NFTs.

## The Hard Way (Quicker, not that hard)
Copy the code provided in the code block below. Paste the following array into the `idata` field using the Atomic Assets [createschema](https://wax.bloks.io/account/atomicassets?loadContract=true&tab=Actions&account=atomicassets&scope=atomicassets&limit=100&action=createschema) action to create your own schema on Atomic Assets, and then create [template](https://wax.bloks.io/account/atomicassets?loadContract=true&tab=Actions&account=atomicassets&scope=atomicassets&limit=100&action=createtemp) from the schema for each NFT you release. 

> ℹ️  Important  

Individual nfts/templates may leave fields blank, but the schema must have every field. You may add fields to the schema later, but not remove them. New fields will appear at the end, thus, best to modify this standard to your needs before deploying.

# 🛠 Web4NFT Metadata Standard
> Works with Atomichub UI out of the box. You can even avoid touching this code by using Create Schema on atomichub to replicate. 

```javascript
[
  {
    "name": "name",
    "type": "string"
  },
  {          
    "name": "title",
    "type": "string"
  },
  {
    "name": "about",
    "type": "string"
  },
  {
    "name": "img",
    "type": "ipfs"
  },
    {
    "name": "clip",
    "type": "ipfs"
  },
  {
    "name": "audio",
    "type": "ipfs"
  },
  {
    "name": "video",
    "type": "ipfs"
  },
  {
    "name": "backimg",
    "type": "ipfs"
  },
  {
    "name": "promo",
    "type": "ipfs"
  },
  {
    "name": "collectionimg",
    "type": "ipfs"
  },
  {
    "name": "timestamp",
    "type": "string"
  },
  {
    "name": "date",
    "type": "string"
  },
  {
    "name": "year",
    "type": "string"
  },
    {
    "name": "month",
    "type": "string"
  },
    {
    "name": "day",
    "type": "string"
  },
  {
    "name": "location",
    "type": "string"
  },
  {
    "name": "nation",
    "type": "string"
  },
  {
    "name": "state",
    "type": "string"
  },
  {
    "name": "city",
    "type": "string"
  },
  {
    "name": "geotag",
    "type": "string"
  },
  {
    "name": "credits",
    "type": "string"
  },
  {
    "name": "license",
    "type": "string"
  },
  {
    "name": "rarity",
    "type": "string"
  }
]
```




# How To Modify this schema  🛠️

When modifying the schema, you can add new fields, but avoid removing existing ones to ensure maximum compatibility.

Ideas:

**Artist** - If you'd rather have your name here than in credits   
**Multiple Media fields** - Duplicate the audio fields to include all songs on an album, etc (First DYOR on marketplace support) 
**Youtube** - Youtube is supported on Atomichub and other marketplaces, leading to an embeded video.   
**More Metadata** - Add custom metadata specific to your field  



# Power of the Schema ✨ 🧙‍♂️
Using this template ensures maximum forward-compatibility with geotemporal "mapps" (Map dApps) like [cXc.world](https://music.cxc.world)

There is a **magical benefit** of this standard in development. Soon [cXc.world](https://music.cxc.world) will track those using this schema in their templates, and automatically generate mapps based on the info on the NFT. For best results, always incluse the ISO country code (three letters).

We will continue to release tools to help others create geographically and temporally aware dApps

# Evolution of the Schema 🚀 🛸

This schema will grow and evolve. Feel free to open issues on this repo with your suggestions.  

If you adapt this schema for another blockchain or NFT standard, please submit a pull request adding a file named <chain>.md in the main directory, containing the necessary deployment code. Alternatively, you can open an issue with the code, and I can update the repository if you prefer.

# Mini Change Log

## 1.0.0 - May 1, 2023
Initial Release of the Standard


# Pomelo Supporters 🍊

Special Thanks to: dansingjoy, mods, markstair, keyes, eosnames, monstredd, ronshek, estebansaa, apporc, martinbreuer, soa432, earthman, eostrace, chuck, hernanarber, dphillippi, denis, stephb, jun, lovejoy, crabnetwork, mikelennie, merivercap, anasalharbi5, donsonzeng, lanhange, joshuaseymour

 <p align="center"> ~ Created with 💜 by <a href="https://cxc.world" alt="cXc.world Music Mapp">cXc</a> ~ <p>
