# Privacy Policy — VsisProxy Chrome Extension

**Effective date:** 2026-05-06
**Last updated:** 2026-05-06
**Live URL:** https://vsis.net/privacy/vsisproxy-extension *(planned)*

VsisProxy ("the extension", "we", "our") is an open-source Chrome extension built by **VSIS.NET** that lets you manage and switch HTTP proxies. We take privacy seriously: VsisProxy is **local-first** and **does not collect any personal data**. This page explains what the extension does, what it stores, and what it never does.

---

## TL;DR

- ✅ All your data (proxies, profiles, auto-switch rules) is stored **only on your own device** and synced via your own Google account using Chrome's built-in `chrome.storage.sync`. We never see it.
- ✅ The extension makes **no network call to VSIS.NET servers**. It is fully usable with any HTTP proxy from any provider.
- ✅ The only outbound network call is the optional **Live Test** feature, which contacts `https://api.ipify.org` to verify a proxy works. This is on-demand, only when you click the test button.
- ❌ We do **not** collect, transmit, sell, share, or analyze your browsing history, traffic, or personal information.
- ❌ We do **not** include any analytics, tracking, advertising, or telemetry SDKs.
- ❌ We do **not** require an account, login, email, or any registration to use the extension.

---

## 1. Data we collect

**None.**

VsisProxy does not collect, transmit, or store any data on our servers. We have no servers that receive your data. We have no database. We have no analytics dashboard. There is nothing for us to delete because we never had it.

---

## 2. Data the extension stores **on your device**

For the extension to function, it stores configuration data using Chrome's built-in storage APIs. This data lives **on your device**; if you sync Chrome through your Google account, Chrome (not us) replicates it to your other Chrome installations.

| Data | Stored in | Synced to your other Chrome devices? | Visible to VSIS.NET? |
|------|-----------|--------------------------------------|----------------------|
| Proxies you added (host, port, optional username/password, label) | `chrome.storage.sync` | Yes — via your Google account | **No** |
| Profiles (name, color, linked proxy) | `chrome.storage.sync` | Yes | **No** |
| Auto-switch rules (URL pattern, type, target profile) | `chrome.storage.sync` | Yes | **No** |
| Default profile selection | `chrome.storage.sync` | Yes | **No** |
| Currently active mode (Off / Fixed / Auto Switch) | `chrome.storage.local` | No (per-device) | **No** |
| Language preference (Auto / English / Tiếng Việt) | `chrome.storage.local` | No (per-device) | **No** |

`chrome.storage.sync` is a Google Chrome feature; the data is encrypted in transit and at rest by Google between your Chrome installations. We have no access to it.

To delete all stored data: uninstall the extension (`chrome://extensions` → Remove). Chrome will purge both `chrome.storage.local` and `chrome.storage.sync` for the extension.

---

## 3. Network calls the extension makes

VsisProxy only makes outbound network calls in two cases:

### 3.1 Through the proxy you configured

When you set a proxy as **Active** (Fixed or Auto Switch mode), Chrome routes your browser traffic through that proxy server. This is the entire point of the extension. VsisProxy itself does not see, log, or transmit the destinations you visit — it merely tells Chrome which proxy to use.

If your proxy requires authentication (`HTTP 407 Proxy Authentication Required`), the extension supplies the username/password you stored. The credentials are sent **directly to your proxy server**, never to VSIS.NET.

### 3.2 The Live Test feature (only when you click the ⚡ button)

When you click **Test** on a proxy, the extension makes a single HTTPS request to:

```
https://api.ipify.org?format=json
```

through the proxy under test, then immediately restores your previous Chrome proxy settings. The response is a short JSON body containing the public IP address as observed by ipify (a free, well-known IP echo service). This lets you verify the proxy is alive and see its outbound IP and latency.

- The request is initiated **only when you explicitly click Test**. It never runs in the background.
- The destination URL is hardcoded in the open-source code at `src/background/index.ts`. You can audit it at https://github.com/vsisnet/vsisproxy-extension
- ipify is operated by an independent third party (Joel Sundström). Their privacy policy: https://www.ipify.org

If you do not want this single network call, simply do not click the Test button.

---

## 4. Permissions the extension requests, and why

The extension is open-source and Manifest V3. Each Chrome permission is requested only because it is required for the corresponding feature; we do not request permissions we do not use.

| Permission | Why it is requested |
|------------|---------------------|
| `proxy` | To set Chrome's proxy settings (Fixed mode and PAC script for Auto Switch). This is the core feature. |
| `storage` | To save proxies, profiles, and rules as described in section 2. |
| `webRequest` | To detect proxy authentication challenges (HTTP 407). |
| `webRequestAuthProvider` | To respond to proxy authentication challenges by supplying the username/password you stored. Required for proxies that need auth. |
| `alarms` | Reserved for an upcoming optional health-check feature; no scheduled alarms run in v0.3.x. |
| `notifications` | Reserved for optional desktop notifications (e.g. when an auto-rotate triggers). Not used in v0.3.x. |
| `<all_urls>` host permission | Required by `webRequest.onAuthRequired` to intercept proxy 407 challenges, which can come from any URL the user navigates to. The extension does not read or modify any web page content; it only handles proxy auth. |

---

## 5. Children's privacy

VsisProxy is not directed at children under 13. We do not knowingly collect any personal information from anyone, regardless of age.

---

## 6. International users (GDPR, CCPA)

Because we do not collect personal data, GDPR data subject requests (access, rectification, erasure, portability) and CCPA consumer requests are answered by uninstalling the extension — Chrome will purge all stored data immediately. We have no separate copy.

---

## 7. Open source verification

The full source code of VsisProxy is published at:

> **https://github.com/vsisnet/vsisproxy-extension**

You can audit every line yourself. The extension is published to the Chrome Web Store using exactly the source in this repository, tagged at the corresponding release version.

If you find any privacy or security issue, please open an issue on GitHub or email us (see Contact below).

---

## 8. Changes to this policy

If this policy changes, the new version will be published at the URL above with an updated "Last updated" date. Material changes will also be announced in the GitHub repository releases page.

---

## 9. Contact

- **Company:** VSIS.NET
- **Website:** https://vsis.net
- **Email:** privacy@vsis.net
- **GitHub Issues:** https://github.com/vsisnet/vsisproxy-extension/issues

---

# Chính sách bảo mật — Tiện ích VsisProxy cho Chrome (Tiếng Việt)

**Ngày hiệu lực:** 06/05/2026
**Cập nhật gần nhất:** 06/05/2026

VsisProxy là tiện ích Chrome mã nguồn mở do **VSIS.NET** phát triển, giúp bạn quản lý và chuyển proxy HTTP. Chúng tôi tôn trọng quyền riêng tư của bạn: VsisProxy hoạt động **cục bộ trên máy bạn** và **không thu thập bất kỳ dữ liệu cá nhân nào**.

## Tóm tắt nhanh

- ✅ Toàn bộ dữ liệu (proxy, profile, auto-switch rules) lưu **chỉ trên thiết bị của bạn** và đồng bộ qua tài khoản Google của bạn bằng `chrome.storage.sync` của Chrome. Chúng tôi không bao giờ thấy.
- ✅ Tiện ích **không gọi tới máy chủ VSIS.NET nào**. Bạn có thể dùng với proxy HTTP bất kỳ từ bất cứ nhà cung cấp nào.
- ✅ Mạng duy nhất tiện ích gọi là tính năng **Live Test** (tự nguyện) — gọi `https://api.ipify.org` để kiểm tra proxy còn sống. Chỉ khi bạn bấm nút Test.
- ❌ Chúng tôi **không** thu thập, gửi đi, chia sẻ, phân tích lịch sử duyệt web, traffic, hay thông tin cá nhân của bạn.
- ❌ Tiện ích **không** dùng bất kỳ SDK analytics, tracking, quảng cáo, hay telemetry nào.
- ❌ **Không** yêu cầu đăng ký tài khoản, email, hay bất kỳ thông tin định danh nào.

## 1. Dữ liệu chúng tôi thu thập

**Không có.**

VsisProxy không thu thập, không gửi đi, không lưu trữ bất kỳ dữ liệu nào trên máy chủ của chúng tôi. Chúng tôi không có máy chủ nhận dữ liệu, không có database, không có dashboard analytics.

## 2. Dữ liệu tiện ích lưu trên thiết bị của bạn

Để hoạt động, tiện ích lưu cấu hình bằng các API storage có sẵn của Chrome. Dữ liệu này nằm **trên thiết bị của bạn**; nếu bạn bật đồng bộ Chrome qua Google account, Chrome (không phải chúng tôi) đồng bộ chúng giữa các Chrome bạn dùng.

| Dữ liệu | Lưu ở | Sync giữa các Chrome của bạn? | VSIS.NET có thấy? |
|---------|-------|-------------------------------|-------------------|
| Proxy bạn thêm (host, port, user/pass, nhãn) | `chrome.storage.sync` | Có (qua Google account) | **Không** |
| Profile (tên, màu, proxy gắn) | `chrome.storage.sync` | Có | **Không** |
| Auto-switch rule (URL pattern, type, profile) | `chrome.storage.sync` | Có | **Không** |
| Profile mặc định | `chrome.storage.sync` | Có | **Không** |
| Mode đang active (Off/Fixed/Auto Switch) | `chrome.storage.local` | Không (per-device) | **Không** |
| Ngôn ngữ (Auto/English/Tiếng Việt) | `chrome.storage.local` | Không | **Không** |

Để xoá toàn bộ dữ liệu: gỡ tiện ích (chrome://extensions → Remove). Chrome sẽ xoá sạch.

## 3. Tiện ích gọi mạng khi nào

Chỉ 2 trường hợp:

**3.1 Qua proxy bạn cấu hình** — khi bạn bật proxy Active (Fixed hoặc Auto Switch), Chrome route traffic browser qua proxy đó. Đây là chức năng chính. Tiện ích chỉ bảo Chrome dùng proxy nào, không thấy/log đích bạn truy cập. Nếu proxy yêu cầu auth, tiện ích gửi user/pass bạn lưu **trực tiếp tới proxy của bạn**, không qua VSIS.NET.

**3.2 Live Test (chỉ khi bạn bấm nút ⚡)** — gọi 1 lần HTTPS đến `https://api.ipify.org?format=json` qua proxy đang test, để biết proxy còn sống và IP ra. Sau đó tiện ích restore lại setting cũ. Không tự chạy nền, chỉ khi bạn bấm.

## 4. Quyền (permissions) tiện ích xin

| Quyền | Tại sao |
|-------|---------|
| `proxy` | Set proxy Chrome (chức năng chính) |
| `storage` | Lưu data theo mục 2 |
| `webRequest` | Phát hiện proxy auth challenge (HTTP 407) |
| `webRequestAuthProvider` | Trả lời auth challenge bằng user/pass bạn lưu |
| `alarms` | Dự phòng cho tính năng health-check sắp tới (chưa dùng v0.3.x) |
| `notifications` | Dự phòng cho desktop notification (chưa dùng v0.3.x) |
| `<all_urls>` | `webRequest.onAuthRequired` cần để intercept 407 từ URL bất kỳ. Tiện ích không đọc/sửa nội dung trang web nào. |

## 5. Trẻ em

VsisProxy không hướng đến trẻ em dưới 13 tuổi. Chúng tôi không cố ý thu thập thông tin của bất kỳ ai, bất kể độ tuổi.

## 6. GDPR / CCPA / quyền của người dùng quốc tế

Vì không thu thập dữ liệu cá nhân, các yêu cầu GDPR (truy cập, sửa, xoá, portability) và CCPA được đáp ứng bằng cách gỡ tiện ích — Chrome xoá sạch ngay lập tức. Chúng tôi không có bản sao nào ở đâu khác.

## 7. Verify mã nguồn mở

Toàn bộ mã nguồn VsisProxy công khai tại: **https://github.com/vsisnet/vsisproxy-extension**

Bạn có thể audit từng dòng. Bản đăng Chrome Web Store dùng đúng source code này, tag theo version release.

## 8. Thay đổi chính sách

Khi thay đổi, version mới sẽ đăng ở URL trên với "Cập nhật gần nhất" mới. Thay đổi quan trọng cũng được công bố trong GitHub releases.

## 9. Liên hệ

- **Công ty:** VSIS.NET
- **Website:** https://vsis.net
- **Email:** privacy@vsis.net
- **GitHub Issues:** https://github.com/vsisnet/vsisproxy-extension/issues
