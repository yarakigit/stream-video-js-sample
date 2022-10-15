RTP_PORT=1234
all:clean
	gst-launch-1.0 -v udpsrc port=$(RTP_PORT) caps = "application/x-rtp, media=(string)video, clock-rate=(int)90000, encoding-name=(string)H264, payload=(int)96", retrieve-sender-address=false ! rtph264depay \
	! h264parse ! mpegtsmux \
	! hlssink max-files=4 \
	target-duration=1 \
	playlist-length=3 \
	location=./segment%05d.ts \
	playlist-location=output.m3u8 \
	playlist-root=./
view:
	gst-launch-1.0 -v udpsrc port=$(RTP_PORT) caps = "application/x-rtp, media=(string)video, clock-rate=(int)90000, encoding-name=(string)H264, payload=(int)96" ! rtph264depay \
	! decodebin ! videoconvert ! autovideosink
clean:
	rm -rf *.ts *.m3u8