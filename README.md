# LinkIt Smart 7688 Wi-Fi multi-role

This the the doc for enabling both Wi-Fi access point and station mode simultaneously on LinkIt Smart 7688.

## Usage

1. Factory reset or configure 7688's Wi-Fi to AP mode.

2. Download [ralink.sh](https://raw.githubusercontent.com/changyuheng/linkit-smart-7688-wifi-multi-role/master/files/lib/netifd/wireless/ralink.sh) to 7688 and replace the built-in file `/lib/netifd/wireless/ralink.sh`.

3. SSH login to 7688's shell.

4. Make sure the downloaded file is executable by executing:

    ```
    chmod +x /lib/netifd/wireless/ralink.sh
    ```

5. Execute the following commands:

    a. Replace `<SSID>` with the Wi-Fi router's name which you want to connect to.

    ```
    uci set wireless.sta.ssid="<SSID>"
    ```

    b. Replace `<KEY>` with the password of the above Wi-Fi router's password.

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

    e. Apply the configs.

    ```
    uci commit
    ```

    f. Reload Wi-Fi settings, make the changes take effect.

    ```
    wifi
    ```
