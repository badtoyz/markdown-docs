#Raspberry Pi MPD music server
>This will get you setup with a MPD server running on a Raspberry Pi at about 30% cpu load for streaming over http.Yoou can edit your files your self or replace the mpd.conf with the one here. it has been striped down to only what is needed.

##Getting started
>You will have to have a full Raspberry Pi setup and in running form. This how to will be based off of raspbian (Debian).
        
        sudo apt-get install mpd mpc flac
        
##Now we have to edit /etc/mpd.conf

If you want to change your music dir then change this value or put your music there for mpd to find

    music_directory 		"/var/lib/mpd/music"

I comment out all of the preset alsa settings (Putting # in front will comment out)

    #audio_output {
    #       type            "alsa"
    #       name            "My ALSA Device"
    #       device          "hw:0,0"        # optional
    #       format          "44100:16:2"    # optional
    #       mixer_type      "hardware"      # optional
    #       mixer_device    "default"       # optional
    #       mixer_control   "PCM"           # optional
    #       mixer_index     "0"             # optional
    #}

This is for the httpd streaming output

    audio_output {
            type            "httpd"
            name            "Raspberry Pi MPD"
            encoder         "flac"                  # optional, vorbis or lame
            port            "8000"
    #       bind_to_address "0.0.0.0"               # optional, IPv4 or IPv6
    #       quality         "5.0"                   # do not define if bitrate is defined
            bitrate         "128"                   # do not define if quality is defined
    #       format          "44100:16:1"
    #       max_clients     "0"                     # optional 0=no limit
    }
    
Uncomment this to look like this (Delete the # from the beginning)
   
    audio_output_format		"44100:16:2"

and

    samplerate_converter		"Fastest Sinc Interpolator"

##Permissions

>Mpd needs to have the permission to access /var/lib/mpd

    sudo chown -R mpd /var/lib/mpd

>Now start the Daemon

    sudo service mpd start

    
##Finishing up

>Now that you have it configured and the right permissions set you need to add music. You will need to put your music in /var/lib/mpc/music or if you changed it place the music files in that dir.

Do these command to finish every thing off

    mpc update
    mpc add /
    mpc play
    
>Now your Raspberry Pi is streaming music over the Raspberry pi's ip address at port 8000
    
    http://<ip adress>:8000

**Contact me**

[Email](mailto:badtoyz@gmail.com) - [Twitter](https://twitter.com/badtoyz) - [Github](https://github.com/badtoyz)

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Creative Commons License" style="border-width:0" src="http://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">Creative Commons Attribution-ShareAlike 4.0 International License</a>.