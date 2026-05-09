# VsisProxy — Firefox Extension Releases

[![Firefox Add-ons](https://img.shields.io/badge/Firefox-AMO-FF7139?logo=firefox)](https://addons.mozilla.org/firefox/addon/vsisproxy/)
[![License: MPL 2.0](https://img.shields.io/badge/License-MPL_2.0-orange.svg)](https://www.mozilla.org/MPL/2.0/)

Tiện ích quản lý + chuyển proxy nhanh trên Firefox của [VSIS](https://vsis.net).
Hỗ trợ HTTP / HTTPS / SOCKS5 / SOCKS4, auto-switch theo URL kiểu SwitchyOmega.

> Repo này chỉ chứa **release artifacts** (file `.xpi` cài cho khách).
> Source code là tài sản nội bộ VSIS — không công khai.

## 🔽 Cài đặt

### Cách 1 — qua Firefox Add-ons Store *(khuyến nghị, sau khi Mozilla approve)*

```
https://addons.mozilla.org/firefox/addon/vsisproxy/
```

### Cách 2 — tải `.xpi` thủ công từ Releases

1. Mở tab **[Releases](https://github.com/vsisnet/vsisproxy-firefox-releases/releases)**
2. Tải file `.xpi` của version mới nhất
3. Mở `about:debugging#/runtime/this-firefox` trong Firefox
4. Click **Load Temporary Add-on…** → chọn file `.xpi`

Lưu ý: bản cài qua `about:debugging` chỉ tồn tại cho đến khi đóng Firefox.
Cài permanent cần qua AMO (cách 1).

## ✨ Tính năng

- Dán proxy nhiều format: `ip:port`, `ip:port:user:pass`, `user:pass@ip:port`, `http://`, `https://`, `socks5://`, `socks4://`
- 1-click chuyển proxy cho cửa sổ Firefox
- **SOCKS5 + user/pass auth** (Firefox-only — Chrome không hỗ trợ)
- Auto-switch theo URL với rule wildcard / host / regex
- Profile có màu + nhãn riêng
- Test proxy trong popup (latency + IP echo)
- UI Tiếng Việt + English

## 🔒 Quyền riêng tư

- Không telemetry, không analytics
- Không inject content script vào trang web
- Không gọi mạng trừ khi user bấm **Test proxy**
- Đầy đủ: [PRIVACY.md](./PRIVACY.md)

## 📞 Hỗ trợ

- Email: [vsisnet@gmail.com](mailto:vsisnet@gmail.com)
- Website: [vsis.net](https://vsis.net)
- Doc: [doc.vsis.net](https://doc.vsis.net)

## 📜 License

[Mozilla Public License 2.0](./LICENSE)