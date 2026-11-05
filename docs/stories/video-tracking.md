# False detections in video tracking

This product turned video into art by drawing the path of moving objects. The product is now stopped, but the work taught me to check results on real footage.

**Problem 1.** The first version passed its checks, but the result looked wrong. The clip had two people, and pose tracking chose the most confident person in each frame, so the path jumped between them.

**Fix 1.** I moved to general object detection with identity tracking (YOLOv8, ByteTrack) and filtered out short tracks and objects that did not move. If nothing is found, the code falls back to pose tracking and then to classic motion detection.

**Problem 2.** A chair "moved" in another clip. A person passed in front of it, and this shifted its detected box.

**Fix 2.** Furniture and similar classes are no longer tracked.

**Lesson.** A passing check does not mean that the result is right. Look at the real output.
