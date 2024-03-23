## JavaScript Snippets

### Snippet 1: Active Inactive Nodej express
```javascript
router.put("/users/:id/status", jwtAuth, async (req, res) => {
  try {
    // Check if the authenticated user is an admin
    if (req.user.userType !== "admin") {
      return res.status(403).json({ success: false, message: "Access denied." });
    }

    const userId = req.params.id;
    const { active } = req.body;

    const user = await User.findByIdAndUpdate(userId, { $set: { active } }, { new: true });

    if (!user) {
      return res.status(404).json({ success: false, message: "User not found." });
    }

    res.status(200).json({ success: true, message: "User status updated successfully." });
  } catch (error) {
    console.error("Error updating user status:", error);
    res.status(500).json({ success: false, message: "Failed to update user status." });
  }
});
```
