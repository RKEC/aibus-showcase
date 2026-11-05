# The first real order failed (fixed)

**Problem.** The first real Etsy order arrived, the automation did not start, and a button showed "Order not found".

**Causes.** I found three causes from the stored order and the worker log:

1. The listing was not connected to a product. The system correctly sent the order to review and alerted me.
2. The "Order not found" message was a bug. With no connected listing, the system created no order item, and the button looked for one. This gave a misleading dead end.
3. The buyer left out the labels that the listing asked for, so the order would have gone to review anyway.

**Fix.** All of this is fixed. The system now reads unlabelled answers only when they are clear, and I approve those orders by hand. The button now checks the stored order again and says exactly what is wrong. The system also stores the full order details, and a new end-to-end test replays this failure.

**Lesson.** The safe path worked, because no bad file went out. The error message was the real fault, because it hid the cause.
