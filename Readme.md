# Network Traffic Capture using `tcpdump` and Wireshark on macOS

This guide provides instructions for using `tcpdump`, a command-line network packet analyzer, and Wireshark, a graphical tool, for capturing and analyzing network traffic on macOS.

## Prerequisites

- **macOS** with a working network interface (Wi-Fi or Ethernet).
- **Administrator (sudo) access** to use `tcpdump` or Wireshark for capturing packets.
- **Homebrew** (optional) for installation.

## 1. Using `tcpdump` on macOS

`tcpdump` is a powerful command-line tool that captures network traffic directly from the terminal. It is pre-installed on macOS.

### Check `tcpdump` Installation

Run the following command to verify `tcpdump` is installed:

```bash
tcpdump --version
```

### Basic Commands

#### 1. **Capture All Traffic on a Network Interface**

```bash
sudo tcpdump -i en0
```
Here, `en0` refers to the default Wi-Fi interface on most Macs. Use `tcpdump -D` to list available interfaces.

#### 2. **Capture Traffic to/from a Specific IP Address**

```bash
sudo tcpdump -i en0 host 192.168.0.1
```
Replace `192.168.0.1` with your desired IP address.

#### 3. **Capture Traffic on a Specific Port**

```bash
sudo tcpdump -i en0 port 80
```
This example captures HTTP traffic on port 80.

#### 4. **Capture and Save Packets to a File**

```bash
sudo tcpdump -i en0 -w capture.pcap
```
This saves the capture to a file named `capture.pcap` for later analysis in Wireshark.

#### 5. **Filter Traffic by Protocol (e.g., TCP)**

```bash
sudo tcpdump -i en0 tcp
```

### Stop Capturing

To stop the capture, press `Ctrl + C` in the terminal.

## 2. Using Wireshark on macOS

Wireshark is a graphical tool for network protocol analysis.

### Installation via Homebrew

Install Wireshark using Homebrew:

```bash
brew install --cask wireshark
```

### Capturing Traffic with Wireshark

1. **Launch Wireshark**: Open Wireshark from your Applications folder.
2. **Select Interface**: Choose the network interface (e.g., Wi-Fi or Ethernet) to start capturing packets.
3. **Filter Traffic**: Use the filter bar to specify protocols (e.g., `tcp`, `http`) or IP addresses.
4. **Stop Capture**: Click the red stop button to stop the capture.
5. **Save Captures**: Save captured data to a `.pcap` file for future analysis.

### Opening Captures from `tcpdump`

Wireshark can open `.pcap` files created by `tcpdump`:

```bash
wireshark capture.pcap
```

## Troubleshooting

- If `tcpdump` shows an error about permissions (e.g., `Operation not permitted`), ensure you are using `sudo` to run the command.
- To list network interfaces, use:
  ```bash
  tcpdump -D
  ```

