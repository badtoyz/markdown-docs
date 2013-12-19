#Raspberry Pi MPD music server
>This will get you setup with a MPD server running on a Raspberry Pi at about 30% cpu load for streaming over http.

##Getting started
>You will have to have a full Raspberry Pi setup and in running form. This howto will be based off of raspbian (debain).
        
        sudo apt-get install mpd mpc flac
        
##Now we have to eddit /etc/mpd.conf

If you want to change your music dir then chage this value or put your music there for mpd to find

music_directory		"/var/lib/mpd/music"




This is for the httpd streaming output

    ```audio_output {
            type            "httpd"
            name            "Raspberry Pi MPD"
            encoder         "flac"                  # optional, vorbis or lame
            port            "8000"
        #       bind_to_address "0.0.0.0"               # optional, IPv4 or IPv6
        #       quality         "5.0"                   # do not define if bitrate is defined
            bitrate         "128"                   # do not define if quality is defined
            #       format          "44100:16:1"
            #       max_clients     "0"                     # optional 0=no limit
            }```