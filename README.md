# Lab M6.01 - Deploy Application with Logging Configuration

## Overview
This project demonstrates a Python Flask API that implements structured JSON logging, which is then analyzed using AWS CloudWatch Logs Insights.

## Architecture
- **App:** Flask/Python using `structlog`.
- **Log Shipping:** Manual injection via AWS CLI (configured for macOS compatibility).
- **Analysis:** CloudWatch Logs Insights QL.

## Setup & Deployment
1. **Environment:** Installed dependencies using `pip3 install -r app/requirements.txt`.
2. **Server:** Started the Flask server on port 5000 (after disabling macOS AirPlay Receiver).
3. **AWS Config:** Created Log Group `/aws/application/api` and Log Stream `my-mac-logs` via AWS CLI.
4. **Data Injection:** Used `aws logs put-log-events` to send structured JSON payloads.

## Screenshots
- Log Group: See `screenshots/01-log-group.png`
- Insights Query: See `screenshots/03-log-insights.png`

## Challenges & Solutions
- **OS Incompatibility:** The CloudWatch Agent `.deb` installer is for Linux. **Solution:** Used AWS CLI to push logs directly.
- **Port Conflict:** macOS uses Port 5000 for AirPlay. **Solution:** Disabled AirPlay Receiver in System Settings.
- **Timestamp Formatting:** Mac `zsh` date syntax differs from Linux. **Solution:** Used `$(($(date +%s)*1000))` for millisecond precision.
