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

## Các điều kiện tiên quyết

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
## Tài nguyên bổ sung


- [3d-printing.md](3d-printing.md) - Pháp y in 3D (G-code nhị phân PrusaSlicer, QOIF, ống co nhiệt)
- [windows.md](windows.md) - Pháp y Windows (registry, SAM, nhật ký sự kiện, thùng rác, luồng dữ liệu thay thế NTFS, nhật ký USN, lịch sử PowerShell, Defender MPLog, cơ chế duy trì WMI, Amcache)
- [network.md](network.md) - Pháp y mạng cơ bản (tcpdump, giải mã keylog TLS/SSL, trích xuất khóa chính TLS từ coredump, Wireshark, PCAP, quét cổng, giải mã SMB3, giao thức 5G/NR, trinh sát WordPress, thông tin xác thực, giấu tin (steganography) qua USB HID, mã hóa BCD, rò rỉ dữ liệu qua tải tệp HTTP, ghép lại tệp nén chia nhỏ dựa trên dấu thời gian)
- [network-advanced.md](network-advanced.md) - Pháp y mạng nâng cao (mã hóa theo khoảng thời gian gói tin, bẻ khóa hash NTLMv2, kênh ngầm qua cờ TCP, giấu tin trong byte cuối cùng của DNS, mã hóa nhị phân vào byte cuối DNS, PCAP đa lớp với XOR + ZIP và khóa mDNS, phân tích lỗi nén (decompression bomb) Brotli, tái sử dụng SMB RID qua LSARPC, trích xuất hash MS-SNTP bằng kỹ thuật Timeroasting, ghép lại dữ liệu dnscat2, bẻ khóa bí mật chia sẻ RADIUS, nhận diện luồng RC4, xoay vòng byte dữ liệu tải (payload) ICMP, kênh ngầm qua độ trễ thời gian ping ICMP)
- [peripheral-capture.md](peripheral-capture.md) - Khôi phục lưu lượng thiết bị ngoại vi USB/HID/Bluetooth (khôi phục nét vẽ chuột/bút USB HID, giải mã dữ liệu bàn phím USB HID, rò rỉ dữ liệu qua mã Morse đèn LED bàn phím USB, theo dõi điều hướng phím mũi tên bàn phím USB HID, ghép lại gói tin Bluetooth RFCOMM)
- [disk-and-memory.md](disk-and-memory.md) - Pháp y đĩa và bộ nhớ cốt lõi (Volatility, gắn/khôi phục dữ liệu đĩa (carving), VM/OVA/VMDK, snapshot VMware, kiểm tra trực quan bản dump bộ nhớ thô bằng GIMP, coredump, phân loại nhanh (triage) bằng Windows KAPE, mã độc tống tiền (ransomware) PowerShell, pháp y Android, pháp y container Docker, pháp y lưu trữ đám mây, khôi phục cấu trúc BSON, gắn ổ đĩa TrueCrypt/VeraCrypt)
- [disk-advanced.md](disk-advanced.md) - Kỹ thuật pháp y đĩa và bộ nhớ nâng cao (phân vùng đã xóa, (Phân tích pháp y ZFS, mã hóa GPT GUID, phân tích tệp VMDK thưa (sparse), trích xuất chuỗi từ bản sao bộ nhớ (memory dump), khôi phục khóa ransomware, XOR macro WordPerfect, khôi phục minidump từ ISO 9660, khôi phục snapshot APFS, khôi phục RAID 5 bằng XOR, khôi phục resource fork HFS+, phân tích pháp y cơ sở dữ liệu băm Kyoto Cabinet, tái tạo lịch sử chỉnh sửa SQLite)
- [disk-recovery.md](disk-recovery.md) - Các mẫu khôi phục và trích xuất dữ liệu đĩa (khôi phục khóa chính LUKS, tấn công vét cạn (brute-force) hạt giống dấu thời gian PRNG, khôi phục nhị phân macro VBA, giải nén FemtoZip, tái tạo hệ thống tệp XFS, trích xuất mục trùng lặp trong tệp tar, trích xuất hệ thống tệp lồng nhau kiểu búp bê Nga (matryoshka), kỹ thuật chống trích xuất (anti-carving) bằng cách chèn byte null, khôi phục subvolume/snapshot BTRFS, khôi phục dữ liệu từ vùng trống FAT16, khôi phục tệp đã xóa trên FAT16 bằng công cụ fls/icat của Sleuth Kit, khôi phục inode mồ côi trên ext2 bằng fsck, sửa lỗi header tệp ZIP bị hỏng)
- [steganography.md](steganography.md) - Giấu tin (steganography) tổng quát (giấu tin ở biên nhị phân, giấu tin đa lớp trong PDF, keyframe SVG, sắp xếp lại thứ tự PNG, dữ liệu đính kèm cuối tệp (file overlays), mã Morse từ sự khác biệt khung hình GIF, GZSteg kết hợp spammimic, khôi phục tần suất từ ​​bảng tính, giải mã giao thức đồ họa terminal Kitty, giấu tin qua chuỗi thoát ANSI, giải mã ảnh nổi 3D (autostereogram), kỹ thuật chèn xen kẽ byte và dòng hai lớp, giấu tin trong container video đa luồng, giải mã XOR theo lớp cho PNG hiển thị dần (progressive PNG), tái tạo mã QR từ hình ảnh phản chiếu bị cong)
- [stego-image.md](stego-image.md) - Giấu tin chuyên biệt cho hình ảnh (giấu tin vào LSB của bảng DQT không sử dụng trong JPEG, trích xuất mã QR từ bitplane BMP, ghép lại mảnh ghép hình ảnh, phát hiện tỷ lệ DCT JPEG bằng thuật toán F5, giấu tin vào mục bảng màu PNG không sử dụng, tái tạo mã QR từ các ô (tile), hoán vị pixel dựa trên hạt giống kết hợp mã QR đa bitplane, ánh xạ pixel sang văn bản từ ảnh thu nhỏ (thumbnail) JPEG, giấu tin LSB có điều kiện kết hợp lọc pixel, tận dụng vùng dư thừa (slack space) JPEG, giấu tin bằng nội suy láng giềng gần nhất (nearest-neighbor), giấu tin bằng tính chẵn lẻ RGB)
- [stego-advanced.md](stego-advanced.md) - Giấu tin nâng cao phần 1: kỹ thuật âm thanh và tín hiệu (miền tần số FFT, âm thanh DTMF, SSTV kết hợp LSB, mã vạch DotCode, bàn phím âm kép tần số tùy chỉnh, kỹ thuật vi sai âm thanh đa rãnh) phép trừ, kỹ thuật LSB đa bit xuyên kênh, nốt nhạc từ FFT âm thanh, mã hóa bát phân (octal) cho siêu dữ liệu âm thanh, mã hóa khoảng trắng trong tệp tar lồng nhau, steganography âm thanh DeepSound kết hợp bẻ khóa mật khẩu, mã hóa nhị phân dạng sóng âm thanh, mã QR ẩn trong phổ âm thanh (spectrogram))
- [stego-advanced-2.md](stego-advanced-2.md) - Steganography nâng cao phần 2: video, biến đổi hình ảnh và các kỹ thuật đặc thù theo định dạng (tích lũy khung hình video, âm thanh đảo ngược, tính trung bình khung hình video, steganography hoán vị TOC trong JPEG XL, giải mã xáo trộn Arnold's Cat Map, giải điều chế FM tùy chỉnh cho SSTV độ phân giải cao, steganography sử dụng byte thừa sau mã FFD9 trong MJPEG, EXIF ​​zlib kết hợp mẫu pixel Stegano, kênh ngầm xref trong PDF, steganography qua mã thoát ANSI, khử trùng lặp ECB ở cấp độ pixel)
- [linux-forensics.md](linux-forensics.md) - Pháp y kỹ thuật số trên Linux/ứng dụng (phân tích log, pháp y ảnh Docker, chuỗi tấn công, thông tin xác thực trình duyệt, lịch sử Firefox, TFTP, TLS dùng RSA yếu, âm thanh qua USB, khôi phục thư mục Git, bẻ khóa KeePass v4, khôi phục Git reflog/fsck squash, phân tích dấu vết trình duyệt (lịch sử Chrome/Chromium/Firefox, cookie, tệp tải xuống, bộ nhớ cục bộ, khôi phục phiên làm việc), sửa lỗi git blob bị hỏng bằng phương pháp vét cạn byte (byte brute-force), trích xuất dữ liệu ô Excel (macro VBA) thành tệp nhị phân ELF, khôi phục mã nguồn Python từ bộ nhớ bằng pyrasite)
- [signals-and-hardware.md](signals-and-hardware.md) - Giải mã tín hiệu phần cứng kèm mã nguồn giải mã (phân tích khung hình VGA, giải mã ký hiệu HDMI TMDS, DisplayPort 8b/10b + giải xáo trộn LFSR), âm thanh từ Voyager Golden Record, giải mã UART bằng Saleae Logic 2, tệp .sub của Flipper Zero, phân tích kênh kề về công suất (DPA), kênh kề âm thanh bàn phím, giấu tin (steganography) trong ảnh đĩa CD âm thanh (giải xen kẽ CIRC + dựng hình xoắn ốc), mã Morse từ đèn LED Caps-lock trong video, phân tích dữ liệu dump keylogger input_event trên Linux, UART nối tiếp từ âm thanh WAV, tái tạo lưới USB MIDI Launchpad

---

## Khi nào cần chuyển hướng

- Nếu bạn khôi phục được một khối dữ liệu mã hóa (encrypted blob) và phần khó nằm ở các thuật toán RSA, AES hoặc mật mã dựa trên lưới (lattice-based cryptography), hãy chuyển sang `/ctf-crypto`.
- Nếu các bằng chứng thực sự liên quan đến giai đoạn chuẩn bị của mã độc (malware staging), trích xuất cấu hình beacon, hoặc các mẫu mã độc đã được đóng gói (packed samples), hãy chuyển sang `/ctf-malware`.
- Nếu dữ liệu thu thập được là bản sao lưu ứng dụng web hoặc bản trích xuất dữ liệu API (API dump), và vấn đề còn lại nằm ở logic ứng dụng, hãy chuyển sang `/ctf-web`.
- Nếu bằng chứng pháp y thực chất là một bài toán giải mã (encoding puzzle), kỹ thuật giấu tin (steganography), hoặc định dạng dữ liệu lạ thay vì các kỹ thuật pháp y truyền thống, hãy chuyển sang `/ctf-misc`.
- Nếu bạn cần truy vết cơ sở hạ tầng, xác định danh tính tác nhân tấn công, hoặc điều tra thông tin công khai dựa trên các kết quả pháp y, hãy chuyển sang `/ctf-osint`.
- Nếu dữ liệu thu thập được là tệp nhị phân đã biên dịch hoặc firmware cần được dịch ngược (disassembly) và phân tích, hãy chuyển sang `/ctf-reverse`.

## Các lệnh bắt đầu nhanh

```bash
# File analysis
file suspicious_file
exiftool suspicious_file     # Metadata
binwalk suspicious_file      # Embedded files
strings -n 8 suspicious_file
hexdump -C suspicious_file | head  # Check magic bytes

# Disk forensics
sudo mount -o loop,ro image.dd /mnt/evidence
fls -r image.dd              # List files
photorec image.dd            # Carve deleted files

# Memory forensics (Volatility 3)
vol3 -f memory.dmp windows.info
vol3 -f memory.dmp windows.pslist
vol3 -f memory.dmp windows.filescan
```

See [disk-and-memory.md](disk-and-memory.md) for full Volatility plugin reference, VM forensics, and coredump analysis.

## Log Analysis

```bash
grep -iE "(flag|part|piece|fragment)" server.log     # Flag fragments
grep "FLAGPART" server.log | sed 's/.*FLAGPART: //' | uniq | tr -d '\n'  # Reconstruct
sort logfile.log | uniq -c | sort -rn | head         # Find anomalies
```

See [linux-forensics.md](linux-forensics.md) for Linux attack chain analysis and Docker image forensics.

## Windows Event Logs (.evtx)

**Key Event IDs:**
- 1001 - Bugcheck/reboot
- 1102 - Audit log cleared
- 4720 - User account created
- 4781 - Account renamed

**RDP Session IDs (TerminalServices-LocalSessionManager):**
- 21 - Session logon succeeded
- 24 - Session disconnected
- 1149 - RDP auth succeeded (RemoteConnectionManager, has source IP)


