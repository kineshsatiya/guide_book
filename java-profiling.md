sudo -u <username> <pid> VM.check_commercial_features

sudo -u <username> jcmd <pid> VM.unlock_commercial_features

sudo -u username jcmd <pid> JFR.start name=MyRecording settings=profile duration=30m filename=/tmp/my-recording.jfr dumponexit=true

sudo -u <username> jcmd <pid> JFR.check
