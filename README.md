# scripts-top_ports.sh
#!/usr/bin/env bash
TARGET="$1"
if [ -z "$TARGET" ]; then echo "Usage: $0 <target>"; exit 1; fi
REPORT_DIR="reports"; mkdir -p "$REPORT_DIR"
TIMESTAMP=$(date +"%Y%m%d_%H%M%S")
OUTPUT_FILE="$REPORT_DIR/top_${TARGET//\//-}_${TIMESTAMP}.txt"
echo "[*] Running top ports scan on $TARGET ..."
nmap -sV --top-ports 100 "$TARGET" -oN "$OUTPUT_FILE"
echo "[+] Scan finished. Saved to $OUTPUT_FILE"
