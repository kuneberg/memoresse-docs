## 1. Apple Subscription (iOS only)

### Behavior - iOS App
- Subscription can be purchased **only on iPhone**
- Correct plan (#1 or #2) is activated
- Usage limits are updated
- Subscription is **Active**
- Subscription **cannot be managed in the app**
  - No change plan
  - No cancel

### Behavior - Web
- Subscription is shown as **Active**
- Correct plan and limits are applied
- **No subscription management**

### What to Verify
- Purchase available only on iOS
- Plan, period, and limits are correct
- No management
- Web shows active subscription without management

---

## 2. Stripe Subscription (Web only)

### Behavior - Web
- Subscription can be purchased **only on Web**
- Correct plan (#1 or #2) is activated
- Usage limits update **immediately**
- Subscription is **Active**
- Subscription **can be managed on Web**
  - Change plan
  - Cancel
  - View payments history

### Behavior - iOS App
- Subscription is shown as **Active**
- Correct plan and limits are applied
- No subscription management

### What to Verify
- Purchase available only on Web
- Plan, period, and limits are correct
- Immediate limit updates after changes
- Management available only on Web
- iOS reflects Stripe subscription correctly

---

## 3. Common Checks

### What to Verify
- Subscriptions are account-specific
- Different accounts do not share subscriptions
- Subscription state is consistent between iOS and Web
- Limits match the active plan
