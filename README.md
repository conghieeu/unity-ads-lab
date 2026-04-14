# 📢 Unity Ads Lab

> 🚧 **Work in Progress** — Early stage, actively being set up.

A hands-on laboratory project for learning and integrating **mobile ad SDKs** in Unity — covering **Google Mobile Ads (AdMob)**, **Unity Ads**, banner ads, interstitials, and rewarded ads — built on the **Universal Render Pipeline (URP)**.

---

## 📖 Overview

This repo serves as a practical reference for integrating ad monetization into Unity mobile games. It covers SDK setup, ad lifecycle management, and best practices for showing ads without disrupting gameplay — targeting **Android and iOS**.

The project uses **URP** as its render pipeline, reflected by the significant amount of ShaderLab and HLSL shader code included from the URP package.

---

## ✨ Topics Covered

| Ad Type | Description |
|---------|-------------|
| 🟦 Banner Ads | Persistent banner at top/bottom of screen |
| ⬛ Interstitial Ads | Full-screen ads shown between game sessions |
| 🎁 Rewarded Ads | Optional ads that reward the player (extra lives, currency, etc.) |
| 🔔 Ad Events | Callbacks for load, show, fail, reward, close |
| 📱 GDPR / Consent | User consent flow for EU compliance |

---

## 🛠️ Tech Stack

| Tool | Details |
|------|---------|
| Engine | Unity (URP template) |
| Language | C# |
| Render Pipeline | Universal Render Pipeline (URP) |
| Ads SDK | Google Mobile Ads (AdMob) / Unity Ads |
| Platform | Android, iOS |

---

## 🚀 Getting Started

### Prerequisites

- [Unity Hub](https://unity.com/download) with **Unity 2022.3 LTS** or newer
- **Android Build Support** module
- **iOS Build Support** module + Xcode (for iOS)
- A Google AdMob account with App ID and Ad Unit IDs

### Clone & Open

```bash
git clone https://github.com/conghieeu/unity-ads-lab.git
```

1. Open **Unity Hub** → **Add project from disk** → select the cloned folder
2. Unity will import all URP packages automatically
3. Open `Assets/Scenes/` and load the main scene
4. Press ▶️ **Play** to test in editor (test ads will load in editor mode)

### Configure Ad IDs

Replace the placeholder IDs in the Ads Manager script with your own:

```csharp
// AdMob App ID — add to AndroidManifest.xml / Info.plist
private const string APP_ID = "ca-app-pub-XXXXXXXXXXXXXXXX~XXXXXXXXXX";

// Ad Unit IDs
private const string BANNER_ID       = "ca-app-pub-XXXXXXXXXXXXXXXX/XXXXXXXXXX";
private const string INTERSTITIAL_ID = "ca-app-pub-XXXXXXXXXXXXXXXX/XXXXXXXXXX";
private const string REWARDED_ID     = "ca-app-pub-XXXXXXXXXXXXXXXX/XXXXXXXXXX";
```

> 💡 Use **test ad unit IDs** from Google during development to avoid policy violations.

---

## 📁 Project Structure

```
Assets/
├── Scenes/
│   └── MainScene.unity          # Demo scene for testing ads
├── Scripts/
│   └── Ads/
│       ├── AdsManager.cs        # Central ads controller (singleton)
│       ├── BannerAdHandler.cs   # Banner ad logic
│       ├── InterstitialAdHandler.cs
│       └── RewardedAdHandler.cs
├── Settings/
│   └── URP/                     # URP renderer & pipeline assets
└── Shaders/                     # Custom URP shaders (HLSL / ShaderGraph)
```

---

## 💡 Usage Example

```csharp
// Show a rewarded ad and grant reward on completion
AdsManager.Instance.ShowRewardedAd(onRewarded: () =>
{
    PlayerInventory.AddCoins(100);
});

// Show interstitial between levels
AdsManager.Instance.ShowInterstitial();

// Load and display a banner
AdsManager.Instance.ShowBanner(BannerPosition.Bottom);
```

---

## 🗺️ Roadmap

- [ ] Google Mobile Ads (AdMob) setup
- [ ] Banner ad integration
- [ ] Interstitial ad integration
- [ ] Rewarded ad integration
- [ ] Ad event callbacks & error handling
- [ ] GDPR consent dialog
- [ ] Unity Ads SDK (alternative provider)
- [ ] Mediation comparison (AdMob vs Unity Ads)
- [ ] Android build & test
- [ ] iOS build & test

---

## 📚 Resources

- 📘 [Google Mobile Ads Unity Plugin](https://github.com/googleads/googleads-mobile-unity)
- 📘 [AdMob Unity Get Started Guide](https://developers.google.com/admob/unity/start)
- 📘 [Unity Ads Documentation](https://docs.unity.com/ads/en-us/manual/UnityAdsHome)
- 📘 [URP Documentation](https://docs.unity3d.com/Packages/com.unity.render-pipelines.universal@latest)
- ⚠️ [AdMob Test Ad Units](https://developers.google.com/admob/unity/test-ads)

---

## ⚠️ Important Notes

- Always use **test ad unit IDs** during development — using real IDs in test builds violates AdMob policies and can get your account suspended
- Real ads only load on **real devices**; the editor uses test/mock ads
- GDPR consent must be implemented before initializing ads if targeting EU users

---

## 📄 License

Personal learning & portfolio project.

---

> Made with ❤️ by [Đoàn Công Hiếu](https://github.com/conghieeu)
