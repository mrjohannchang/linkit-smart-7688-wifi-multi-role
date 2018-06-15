# LinkIt Smart 7688 Wi-Fi multi-role

This is a doc for enabling both Wi-Fi access point and station mode simultaneously on LinkIt Smart 7688.

## Usage

1. Do a factory reset or configure 7688's Wi-Fi to AP mode.

2. Download [ralink.sh](https://raw.githubusercontent.com/changyuheng/linkit-smart-7688-wifi-multi-role/master/files/lib/netifd/wireless/ralink.sh) to 7688 board and replace the built-in file `/lib/netifd/wireless/ralink.sh`.

3. SSH log into 7688's shell.

4. Make the downloaded file executable by executing:

    ```
    chmod +x /lib/netifd/wireless/ralink.sh
    ```

5. Execute the following commands:

    a. Replace `<SSID>` with the SSID on the Wi-Fi router you want to connect to.

    ```
    uci set wireless.sta.ssid="<SSID>"
    ```

    b. Replace `<KEY>` with the corresponding password of the above SSID.

    ```
    uci set wireless.sta.key="<KEY>"
    ```

    c. Set encryption type to WPA-PSK.

    ```
    uci set wireless.sta.encryption="psk"
    ```

    d. Enable Wi-Fi station mode.

    ```
    uci set wireless.sta.disabled="0"
    ```

    e. Apply the modified config.

    ```
    uci commit wireless
    ```

    f. Reload Wi-Fi settings, make the change take effect.

    ```
    wifi
    ```
