RTP_PORT=1234
all:
	gst-launch-1.0 -v udpsrc port=$(RTP_PORT) caps = "application/x-rtp, media=(string)video, clock-rate=(int)90000, encoding-name=(string)H264, payload=(int)96" ! rtph264depay \
	! h264parse ! mpegtsmux \
	! hlssink max-files=8 target-duration=5 \
	location=./segment%05d.ts \
	playlist-location=output.m3u8 \
	playlist-root=./