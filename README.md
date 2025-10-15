# Smart App Store Redirect

A single shareable link that automatically detects the user's device and opens the appropriate app store directly (Google Play Store for Android, App Store for iOS).

## Features

- 🔍 **Automatic Device Detection**: Detects Android, iOS, and desktop devices
- 📱 **Direct App Store Opening**: Uses URL schemes to open the native app store apps
- ⚡ **Instant Redirect**: No countdown - immediate redirection
- 🔄 **Smart Fallbacks**: Falls back to web URLs if URL schemes fail
- 🎯 **Manual Options**: Provides manual buttons for desktop/unknown devices
- 📱 **Mobile Optimized**: Clean, minimal interface perfect for mobile sharing

## How It Works

1. **Device Detection**: Analyzes the user agent to detect Android/iOS devices
2. **URL Scheme Attempt**: Tries to open the native app store using URL schemes:
   - Android: `market://details?id=com.yourapp.package`
   - iOS: `itms-apps://itunes.apple.com/app/id123456789`
3. **Web Fallback**: If URL schemes fail, redirects to web app store URLs
4. **Manual Fallback**: Shows buttons for desktop users or when detection fails

## Setup Instructions

1. **Replace App Store URLs**: 
   - Open `index.html` and find the `APP_CONFIG` object
   - Replace the placeholder URLs with your actual app store links:
     ```javascript
     const APP_CONFIG = {
         android: {
             playStoreUrl: 'https://play.google.com/store/apps/details?id=com.yourapp.package',
             marketUrl: 'market://details?id=com.yourapp.package',
             appName: 'Your App Name'
         },
         ios: {
             appStoreUrl: 'https://apps.apple.com/app/your-app-name/id123456789',
             itmsUrl: 'itms-apps://itunes.apple.com/app/id123456789',
             appName: 'Your App Name'
         }
     };
     ```

2. **Deploy**: 
   - Upload `index.html` to your web server
   - Or use any static hosting service (GitHub Pages, Netlify, Vercel, etc.)

3. **Share**: 
   - Share the single URL - it will automatically detect and redirect users
   - Perfect for QR codes, social media, email campaigns, etc.

## URL Schemes Explained

### Android
- **Primary**: `market://details?id=com.yourapp.package` - Opens Google Play Store app directly
- **Fallback**: `https://play.google.com/store/apps/details?id=com.yourapp.package` - Opens in browser

### iOS  
- **Primary**: `itms-apps://itunes.apple.com/app/id123456789` - Opens App Store app directly
- **Fallback**: `https://apps.apple.com/app/your-app-name/id123456789` - Opens in browser

## Browser Support

- ✅ Chrome (Android & Desktop)
- ✅ Safari (iOS & Desktop) 
- ✅ Firefox (Android & Desktop)
- ✅ Edge (Desktop)
- ✅ Samsung Internet (Android)

## Example Usage

Once deployed, users can simply visit your redirect URL and they'll be automatically taken to the right app store based on their device. Perfect for:

- QR codes on marketing materials
- Social media links
- Email campaigns
- Website banners
- SMS messages

## Testing

To test the functionality:

1. **Android**: Open the link on an Android device - should open Google Play Store app
2. **iOS**: Open the link on an iPhone/iPad - should open App Store app  
3. **Desktop**: Open the link on desktop - should show manual selection buttons

## Troubleshooting

- **Not opening app store app?**: The URL scheme might not be supported - the web fallback will work
- **Wrong device detected?**: The detection logic handles most cases, but manual buttons provide fallback
- **Styling issues?**: Ensure your web server serves the HTML file correctly

## Customization

- **Styling**: Modify the CSS in the `<style>` section to match your brand
- **Timing**: Adjust the timeout in `tryUrlScheme()` function if needed
- **App Information**: Update app names and URLs in the `APP_CONFIG` object

---

**Ready to use!** Just update the app store URLs and deploy. Your single shareable link will automatically open the right app store for each user! 🚀
