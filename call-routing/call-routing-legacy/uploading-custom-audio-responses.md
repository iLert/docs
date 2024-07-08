---
description: >-
  Besides generating IVR menus dynamically or providing fixed text to speech
  feedback, it is possible to upload customised audio files that are played
  back, when callers call call routing numbers.
---

# Uploading custom audio responses

## Configuring custom audio playback

Navigate to **Alert sources -> Call routing** and open the edit view of the desired call routing number which you want to configure.

{% hint style="info" %}
If you have no call routing number yet, [reach our to our support](../../contact.md) to get a custom number for your local area.
{% endhint %}

In the edit view you will find 3 upload options, always on the right side of the configuration options. You may upload:

* an individual greeting for each caller (as replacement for the IVR menu)
* your custom hold music (as replacement for our default hold music)
* a customized mailbox greeting (as replacement for your TTS mailbox text)

![Simply click on Browse.. and choose your MP3 or WAV file](<../../.gitbook/assets/image (59).png>)

Please dont forget to click **Save** when you are done with your configuration.

{% hint style="danger" %}
Please note that you cannot simply use any audio file format, because there is a high chance the file that you are using is not meant to be transcoded for the telephone network, this might result in a poor audio quality or even static noises during playback. Please see the section below for an explanation and even export guide.
{% endhint %}

## Picking the right audio file for the upload

When the audio file that has been uploaded is played back for the first time, it will be automatically transcoded into a format that is optimized for the telephone networks. However depending on the orignal file this may result in issues e.g. poor quality or static noise - we also recommend to check the playback after an upload has been made, hence an additional warning message will be shown in ilert.

The best results are achieved if the uploaded file is already in a **lossless audio format** with a low bitrate e.g. **16 or better 8 bit.**

## Converting your audio files

The following is a guide that helps you to convert or prepare your audio files for an upload in case you have no expert handy. The guide uses the free open source tool Audacity.

### Download Audacity

You may download Audacity [here](https://www.audacityteam.org/). Note: ilert GmbH is not affiliated with Audacity and cannot provide any guarantees or service/support, you are downloading and using it at your own risk.

### Import your audio file

![](<../../.gitbook/assets/Screenshot 2022-05-04 at 13.01.54.png>)

Open up Audacity and drag and drop your audio file into the timeline, it will be imported. (You should be able to use any kind of modern audio format).

### Cut your audio file (optional)

![](<../../.gitbook/assets/Screenshot 2022-05-04 at 13.05.04.png>)

This is an **optional** step, but in case your audio file is longer than needed, you may select the desired audio area by pressing down the left mouse on the timeline and drag it to desired end. Now click on the Scissors icon on the top-middle header (your selection has now been cut out) .Then remove the rest of the timeline, use the X icon on the left side. Then press Strg+V to copy the cut out sequence back into the timeline.

![](<../../.gitbook/assets/Screenshot 2022-05-04 at 13.08.32.png>)

### Converting the audio content from Stereo to Mono

Most likely your audio file will be in Stereo. If it is already in Mono you may skip this step.

![](<../../.gitbook/assets/Screenshot 2022-05-04 at 16.38.10.png>)

Left-click on the drop down next to the name of your audio in the timeline. And click on **Split Stereo to Mono**. _You will now end up with two channels on the timeline_, **make sure to delete one of them** (by clicking on the X icon next to the dropdown arrow that you have used before).

### Exporting your audio file

![](<../../.gitbook/assets/Screenshot 2022-05-04 at 16.44.04.png>)

In the top bar go to **File -> Export -> Export Audio...** from the **File type** drop down select **WAV** as container. And in the **Encoding** selection choose **Unsigned 8-bit PCM** (if possible you may also choose **GSM 6.10**, however this will not allowe test playback in the browser after upload, but it might provide even better audio quality during the live call).

Thats it, upload your exported file to your ilert call routing number and you are done.
