<!-- Add a video element to display the webcam stream -->
<video id="webcam" width="320" height="240"></video>

<!-- Add a canvas element to draw the face detection results -->
<canvas id="overlay" width="320" height="240"></canvas>

<!-- Add a script to access the webcam and draw the face detection results -->
<script>
  // Get the video and canvas elements
  const video = document.getElementById('webcam');
  const canvas = document.getElementById('overlay');
  const context = canvas.getContext('2d');

  // Define the face detection options
  const options = {
    minConfidence: 0.5
  };

  // Create a FaceDetector object
  const detector = new FaceDetector(options);

  // Get the user's webcam stream
  navigator.mediaDevices.getUserMedia({ video: true })
    .then(stream => {
      // Display the stream in the video element
      video.srcObject = stream;

      // Start a loop to detect and draw faces
      setInterval(async () => {
        // Detect the faces in the video frame
        const faces = await detector.detect(video);

        // Clear the canvas
        context.clearRect(0, 0, canvas.width, canvas.height);

        // Draw a rectangle around each face
        faces.forEach(face => {
          const { width, height, top, left } = face.boundingBox;
          context.strokeStyle = 'yellow';
          context.lineWidth = 2;
          context.strokeRect(left, top, width, height);
        });
      }, 1000);
    })
    .catch(error => {
      console.error(error);
    });
</script>
