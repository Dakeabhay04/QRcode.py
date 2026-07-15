import qrcode

# Get user input
upi_id = input("Enter UPI ID: ")
recipient_name = input("Enter Recipient Name: ")
amount = input("Enter Amount (leave blank for any amount): ")

# Create UPI payment URL
upi_url = f"upi://pay?pa={upi_id}&pn={recipient_name}"

# Add amount if provided
if amount.strip():
    upi_url += f"&am={amount}&cu=INR"

# Generate QR Code
qr = qrcode.make(upi_url)

# Save QR Code
file_name = "upi_payment_qr.png"
qr.save(file_name)

print(f"\nQR code saved as '{file_name}'")

# Display QR Code
qr.show()
