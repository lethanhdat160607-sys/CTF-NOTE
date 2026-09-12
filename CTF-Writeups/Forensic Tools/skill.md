---
name: ctf-forensics
description: Cung cấp các kỹ thuật điều tra số và phân tích tín hiệu cho các thử thách CTF. Sử dụng khi phân tích ảnh đĩa (disk image), bản sao bộ nhớ (memory dump), nhật ký sự kiện, dữ liệu bắt gói tin mạng, giao dịch tiền mã hóa, kỹ thuật giấu tin (steganography), phân tích tệp PDF, Windows Registry, Volatility, PCAP, ảnh Docker, core dump, biểu đồ tiêu thụ điện năng (side-channel power trace), phổ âm thanh DTMF, phân tích thời gian gói tin, ảnh đĩa âm thanh CD, hoặc khôi phục tệp và thông tin xác thực đã bị xóa.
license: MIT
compatibility: Yêu cầu tác nhân (agent) hoạt động trên hệ thống tệp (như Claude Code hoặc tương đương) có hỗ trợ bash, Python 3 và kết nối internet để cài đặt công cụ.
allowed-tools: Bash Read Write Edit Glob Grep Task WebFetch WebSearch
metadata:
user-invocable: "false"
---

# CTF Forensics & Blockchain

Tài liệu tham khảo nhanh cho các thử thách CTF thuộc mảng pháp y kỹ thuật số (forensics). Mỗi kỹ thuật được tóm tắt trong một dòng tại đây; vui lòng xem các tệp đính kèm để biết chi tiết đầy đủ.

## Prerequisites

**Python packages (all platforms):**
```bash
pip install volatility3 Pillow numpy matplotlib
```

**Linux (apt):**
```bash
apt install binwalk foremost libimage-exiftool-perl tshark sleuthkit \
  ffmpeg steghide testdisk john pcapfix
```

**macOS (Homebrew):**
```bash
brew install binwalk exiftool wireshark sleuthkit ffmpeg \
  testdisk john-jumbo
```

**Ruby gems (all platforms):**
```bash
gem install zsteg
```

