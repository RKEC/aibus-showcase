# Stopped products could still be ordered

**Problem.** I decided to sell only two products and stopped the others. The `is_active` setting only hid a product from the list. No order route checked it.

**Fix.** Every route that creates an order now returns `409` for a stopped product, before it writes any data. If an old Etsy listing still sells a stopped product, the order is not rendered and I get an alert. I tested this with a real order request.

**Lesson.** A setting that hides something does not enforce anything. Check the rule at the place where the action happens.
