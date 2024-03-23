

# Table of Contents

- [Headers](#headers)
- [JavaScript Snippets](#javascript-snippets)

## Headers

<!-- Content related to Headers -->

## JavaScript Snippets

<details>
  <summary>Snippet 1: Active Inactive Node.js</summary>
  <pre><code>
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



  </code></pre>
</details>

<details>
  <summary>Snippet 2: Delete API with Integration</summary>
  <pre><code>
/* JavaScript code for Snippet 2 */
// Place your JavaScript code here
  </code></pre>
</details>



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


### Snippet 2 : Delete api with integration 
```javascript
/* 1. Nodejs */
router.delete("/users/:userId", jwtAuth, async (req, res) => {
  try {
    // Check if the user is an admin
    if (req.user.userType !== "admin") {
      // If the user is not an admin, send a 403 Forbidden response
      return res.status(403).json({ success: false, message: "Access denied." });
    }

    const userId = req.params.userId;

    // Find the user in the database
    const user = await User.findById(userId);

    // Check if the user exists
    if (!user) {
      return res.status(404).json({ success: false, message: "User not found." });
    }

    // Delete the user from the database
    await User.findByIdAndDelete(userId);

    res.status(200).json({ success: true, message: "User deleted successfully." });
  } catch (error) {
    console.error("Error deleting user:", error);
    res.status(500).json({ success: false, message: "Failed to delete user." });
  }
}); 

/* 2. react function */

const deleteFarmer = () => {
            axiosInstance.delete("/api/auth/users/"+ toBeDeletedUser._id).then(res => {
                if (res.data?.success) {
                    toast.success(` investor  '${toBeDeletedUser.name }'  Deleted!`);
                    getAllUsers()
                    setToBeDeletedUser(null);
                    setOpen(false);
                }
            }).catch(e => {
                if (e.response?.data) {
                    toast.error(e.response.data.message);
                } else {
                    toast.error("Server Error!");
                }
            })
        }
    // call function 
<Tooltip title="Delete User" arrow>
                                            <IconButton
                                              sx={{
                                                '&:hover': { background: theme.palette.error.light },
                                                color: theme.palette.error.main
                                              }}
                                              color="inherit"
                                              size="small"
                                              onClick={() => { setToBeDeletedUser(usr) }}
                                            >
                                              <DeleteTwoToneIcon fontSize="small" />
                                            </IconButton>
                                          </Tooltip>
```


