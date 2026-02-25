<img width="1918" height="910" alt="Screenshot 2026-02-25 143245" src="https://github.com/user-attachments/assets/69a23d28-71ac-4996-9ff9-7df0ab1c013d" />


✅ Method 1: S3 Static Website Hosting (Best for HTML/CSS/JS)
🔹 Step 1: ZIP Extract Cheyyi

Mundu Solar-system-explorer.zip ni extract cheyyi.

Lopala index.html file undali (main page).

🔹 Step 2: S3 Bucket Create Cheyyi

AWS Console → S3

Create Bucket click cheyyi

Bucket name → solar-system-explorer-unique-name

Region → Mumbai (ap-south-1) select cheyyachu

“Block all public access” → ❌ uncheck cheyyi

Create Bucket

🔹 Step 3: Files Upload Cheyyi

Bucket open cheyyi

Upload → extracted files (HTML, CSS, JS, images anni) select cheyyi

Upload complete avvali

🔹 Step 4: Static Website Hosting Enable Cheyyi

Bucket → Properties

Scroll down → Static Website Hosting

Enable

Index document → index.html

Save

Ikkada neeku oka Website Endpoint URL vastundi.

Example:

http://solar-system-explorer.s3-website-ap-south-1.amazonaws.com

Adhi open chesthe nee website live avuthundi 🎉

🔹 Step 5: Public Access Policy Add Cheyyi (Important) --> if bucket is private then you use this step

Bucket → Permissions → Bucket Policy → Paste this:

{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}

your-bucket-name place lo nee bucket name pettu.

Save ✅

🔄 Website Update Ela Cheyyali?

Future lo changes chesina tarvatha:

HTML file edit cheyyi

S3 bucket ki malli upload cheyyi

Existing file replace avuthundi

Browser lo refresh cheyyi

Deploy automatic ga avuthundi.


note : if u getting any error make sure file must be "public acl enable" make enable
