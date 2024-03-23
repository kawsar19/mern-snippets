## JavaScript Snippets

### Snippet 1: Active Inactive Nodej express
```javascript
/* 1. Nodejs */
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

/* 2. react function */

const handleActive = async (event, userId) => {

        try {
          const active = event.target.checked;
      
          // Send a request to update the user's active status
          await axiosInstance.put(`/api/auth/users/${userId}/status`, { active });
          toast.success('User active status updated successfully!');
          getAllUsers()
      
          // Handle the success or display an appropriate message
          // You can refresh the user data or update the specific user's active status in the local state
        } catch (error) {
            toast.error('Error updating user active status:', error);
          // Handle the error or display an error message
        }
    };
    // call function 
    <TableCell align="left">
                        <Switch {...label} defaultChecked={usr.active} onChange={(e) => handleActive(e,usr._id)} />
                      </TableCell>
```


