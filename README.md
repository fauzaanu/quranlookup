## بِسْمِ ٱللّٰهِ ٱلرَّحْمٰنِ ٱلرَّحِيْ
# Obsidian Quran Lookup Plugin

This is a simple utility/text replacement plugin for Obsidian that fills in the quran ayaat (verses) based on a surah:verse(s) shorthand. This uses the 'current editor selection command' capability to replace the selected text with the lookup result.

It looks up based on `Surah-Number:Ayah-Number` or `Surah-Name:Ayah-Number` syntax. For the Surah-Name lookup it uses Fuse.js to do a "fuzzy search" since it's an english transliteration. It replaces that syntax with an Obsidian call-out showing verse+ayah name, arabic, and english.

## How to Use:
1. Open a Note in Obsidian.md
2. In the note, type the `surah:verse` as shown in the examples below
3. Select the recently typed text 
4. In the command panel (cmd+P or ctrl+P) select 'Retrieve Ayat' command
5. Alternatively, you can assign a hotkey to the command (like cmd+shift+k)

## Examples
- Single Ayah lookup
  - `112:1`

![obsidian quran lookup single](/docs/quran-lookup-single.gif?raw=true)

- Multiple Ayaat range
  - `56:24-26`

![obsidian quran lookup range](/docs/quran-lookup-range.gif?raw=true)

- Fuzzy search surah title
  - `Zumar:3-5`
  - `Zomar:3`
  - `Zumaar:6`

- Chained together in single line (separated by spaces)
  - `Zumar:12 6:10-11 7:3-4 Maryam:12 1:3`

![obsidian quran lookup range](/docs/quran-lookup-chained.gif?raw=true)

## Settings
This plugin has some small customizations: in `Community Plugins > Installed Plugins > QuranLookup (Options)`

![obsidian quran lookup settings](/docs/settings.png?raw=true)

### Translation Types
- You can choose from a variety of english translation types based on the [API language selections](http://api.alquran.cloud/v1/edition/language/en):

  | Option | Translator |
  | ------------| ---------|
  | en.ahmedali | Ahmed Ali|
  | en.ahmedraza | Ahmed Raza Khan|
  | en.arberry | A. J. Arberry|
  | en.asad | Muhammad Asad|
  | en.daryabadi | Abdul Majid Daryabadi|
  | en.hilali | Muhammad Taqi-ud-Din al-Hilali and Muhammad Muhsin Khan|
  | en.pickthall | Mohammed Marmaduke William Pickthall|
  | en.qaribullah | Hasan al-Fatih Qaribullah and Ahmad Darwish|
  | en.sahih | Saheeh International|
  | en.sarwar | Muhammad Sarwar|
  | en.yusufali | Abdullah Yusuf Ali|
  | en.maududi | Abul Ala Maududi|
  | en.shakir | Mohammad Habib Shakir|
  | en.transliteration | English Transliteration|
  | en.itani | Clear Qur'an by Talal Itani |

### Remove Parenthesis Contents
- Many translations add additional commentary and explanation in parenthesis and brackets to make the english more readable or flow or to better explain a complex word. If enabled, this feature removes that additional text so that the translation succinct.

![obsidian quran remove paren](/docs/quran-lookup-remove-paren.png?raw=true)

## The Quran API and Source(s)
The Quran verses are currently powered by
- [alquran.cloud](https://alquran.cloud/api) : An opensource Quran API made by the [Islamic Network](https://islamic.network/) ([github](https://github.com/islamic-network)) and respective [contributors](https://alquran.cloud/contributors).
## Fuzzy Search
The Fuzzy search feature is made possible using
- [Fuze.js](https://fusejs.io/) : A powerful lightweight fuzzy-search library, with zero dependencies ([github](https://github.com/krisk/Fuse))
## How to use
- Install & enable the plugin (see [section below](#manually-installing-the-plugin) )
- Select the ayah reference string in your note
- Use the command palette or a hotkey to apply the replace command

## How it works
The lookup uses api.alquran.cloud API to lookup the verses by surah and verse number
For the fuzzy name search, it uses a simple index file surahSlim.json and fuse.js to find the closest sura name and retrieve it's index number.

## Future Feature Ideas
- [ ] Add error handling for 'surah not found' or 'ayah index out of range'
- [ ] Show the translator name in the settings
- [ ] Toggle Display Arabic Only, English Only
- [ ] Right-To-Left alignment for Arabic text
- [ ] Allow for customization of the Call-out style in the settings (e.g. abstract, info, note, success, question, warning, failure, danger, bug, example, quote, none)
- [ ] Give option to show dialog with preview and style options each time (like Admonitions 'Insert Admonition' dialog)
- [ ] Add option to toggle to use 'Admonition' style syntax instead of obsidian call-out style
- [ ] Provide links to ayah in website like quran.com
- [ ] "Offline Mode" which retrieves from a locally saved vault rather than calling API
- [ ] Add audio play button to playback the verse
- Others... feel free to suggest!
## Manually installing the plugin

- Copy over `main.js`, `styles.css`, `manifest.json` to your vault `VaultFolder/.obsidian/plugins/quranlookup/`.
- Reload Obsidian to load the new version of your plugin.
- Enable plugin in settings window.

## How to Contribute
I'm one person who just quickly put this together because I wanted this capability in my notes. This is still in need of much refactoring and improvement.
- [For Issues or Feature Requests](https://github.com/milkperson/quranlookup/issues)
- [For making Contributions](./CONTRIBUTING.md)

## Similar Projects
- [Obsidian Quran Vault](https://github.com/AmmarCodes/obsidian-quran-vault)
- [Obsidian Bible Reference](https://github.com/tim-hub/obsidian-bible-reference) - Notable mention, I styled this readme doc after theirs.