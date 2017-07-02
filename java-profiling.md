sudo -u username jcmd pid JFR.start name=MyRecording settings=profile delay=20s duration=30m filename=\tmp\myrecording-2.jfr dumponexit=true
sudo -u username jcmd pid VM.check_commercial_features
sudo -u username jcmd 13447 JFR.check
