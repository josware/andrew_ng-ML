# andrew_ng-ML
Notes from Andrew's NG popular Machine Learning class from Stanford (Coursera)


## Tips
Add Octave to path:
* Get your octave's path (usally displayed on the top when running octave-cli i.e. ~$/usr/local/octave/3.8.0/bin/octave-3.8.0
* Edit ~/.bash_profile i.e. vi ~/.bash_profile
* add an "alias" to octave i.e. alias octave="/usr/local/octave/3.8.0/bin/octave-3.8.0"
* reload your changes i.e. source ~/.bash_profile

Now you can use octave from the CLI

Another issue I had is with GNUplot, (AquaTerm error) to solve it this worked for me:

* echo "setenv("GNUTERM","qt")" > ~/.octaverc 

Also there are some other interesting solutions here:
https://stackoverflow.com/questions/13786754/octave-gnuplot-aquaterm-error-set-terminal-aqua-enhanced-title-figure-1-unk
