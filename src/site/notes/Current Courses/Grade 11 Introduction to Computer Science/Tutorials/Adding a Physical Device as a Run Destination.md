---
{"dg-publish":true,"permalink":"/current-courses/grade-11-introduction-to-computer-science/tutorials/adding-a-physical-device-as-a-run-destination/","dgHomeLink":false}
---

# Adding a Physical Device as a Run Destination

To run applications you write in Xcode on your iPhone or iPad, a few *one-time-only* setup steps are required.

First, be sure Xcode is open.

Select the menu sequence **Window** → **Devices and Simulators**.

Then, connect your iPhone or iPad to your Mac using a cable.

The first time you do this, you will see an image something like this:

![Screen Shot 2022-10-31 at 7.09.22 AM.png](/img/user/Attachments/Screen%20Shot%202022-10-31%20at%207.09.22%20AM.png)

To test applications you write on a physical device the device must be in *developer mode*. 

> [!NOTE]
> The instructions that follow are for **iOS 16.**
> If you have an earlier version of iOS on your phone, try [these instructions instead](https://www.russellgordon.ca/tutorials/adding-a-physical-device-as-a-run-destination/).

To do this, first open the **Settings** app, then select **Privacy & Security**:

![IMG_1521 copy.png|400](/img/user/Attachments/IMG_1521%20copy.png)

Then select **Developer Mode**:

![IMG_1522 copy.png|400](/img/user/Attachments/IMG_1522%20copy.png)

Then restart your iPhone:

![IMG_1523 copy.png|400](/img/user/Attachments/IMG_1523%20copy.png)

> [!NOTE]
> Despite the warning about reduced device security, know that an application cannot be loaded on to your phone unless it is unlocked and you have explicitly indicated that you trust the developer who wrote the app.

After restarting your phone, you will see this message appear – select **Turn on**:

![IMG_1524 copy.png|400](/img/user/Attachments/IMG_1524%20copy.png)

You will need to provide your device passcode:

![IMG_1525 copy.png|400](/img/user/Attachments/IMG_1525%20copy.png)

Now that you have enabled developer mode on your phone, back in Xcode in the **Devices and Simulators** dialog, you will see a yellow banner message telling you that certain required files are being copied to and from your device:

![Screen Shot 2022-10-31 at 7.14.04 AM.png](/img/user/Attachments/Screen%20Shot%202022-10-31%20at%207.14.04%20AM.png)

That process may take a few minutes to complete; be patient. When it is finished, the yellow banner will disappear.

Next, you can select the device you've connected as a run destination.

At the top of the primary Xcode window, click the list of devices (1), then select your device from the list (2):

![Screen Shot 2022-10-31 at 7.35.54 AM.png](/img/user/Attachments/Screen%20Shot%202022-10-31%20at%207.35.54%20AM.png)

Now build the application:

![Screen Shot 2022-10-31 at 7.37.00 AM.png](/img/user/Attachments/Screen%20Shot%202022-10-31%20at%207.37.00%20AM.png)

Next, will likely see a message indicating that Xcode cannot run the application on the device, because, essentially, your iPhone or iPad currently does not "trust" the Mac that you are developing on to install applications upon it:

![Screen Shot 2022-10-31 at 7.39.02 AM.png|300](/img/user/Attachments/Screen%20Shot%202022-10-31%20at%207.39.02%20AM.png)

On your phone, you will see a message like this:

![IMG_1526.png|400](/img/user/Attachments/IMG_1526.png)

To create the necessary trust, follow these steps.

Open **Settings** again, and choose **General**:

![IMG_1527.png|400](/img/user/Attachments/IMG_1527.png)

Then select **VPN &  Device Management**:

![IMG_1528.png|400](/img/user/Attachments/IMG_1528.png)

Under **Developer App**, you will see a profile tied to your LCS Apple ID – select that profile:

![IMG_1529.png|400](/img/user/Attachments/IMG_1529.png)

To run apps you make using your LCS Apple ID on your device, select the button as shown:

![IMG_1530.png|400](/img/user/Attachments/IMG_1530.png)

Finally, on the dialog that appears, select **Trust**:

![IMG_1531.png|400](/img/user/Attachments/IMG_1531.png)

The next time you build your application with your iPhone or iPad as the selected run destination, after a few seconds, you should see the app open on your device.

Have fun! 🚀
