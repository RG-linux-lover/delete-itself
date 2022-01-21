# delete-itself
The script can delete itself via the shred command (as a secure deletion) when it exits.


#!/bin/bash

currentscript="$0"

# Function that is called when the script exits:
function finish {
    echo "Securely shredding ${currentscript}"; shred -u ${currentscript};
}

# Do your bashing here...

# When your script is finished, exit with a call to the function, "finish":
trap finish EXIT
