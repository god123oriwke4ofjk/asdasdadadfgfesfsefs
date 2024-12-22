
config_file=".config/fastfetch/config.jsonc"
line=$(grep -o 'source": "~/.config/fastfetch/lain[0-9]\+.png",' "$config_file")
lain_number=$(echo "$line" | sed -n 's/.*lain\([0-9]*\).*/\1/p') 
if [ "$lain_number" -ge 6 ]; then
    lain_number=1
else
    lain_number=$((lain_number+1))
fi
sed -i "s/lain[0-9]\+\.png/lain${lain_number}.png/" $config_file 
