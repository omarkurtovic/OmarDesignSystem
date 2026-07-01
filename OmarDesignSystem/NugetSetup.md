Here are the steps outlined for setting up a NuGet package for the Omar Design System



Generate a GitHub Personal Access Token (PAT)

Go to GitHub.com -> Click your Profile Picture -> Settings -> Developer Settings (at the very bottom of the left menu).

Click Personal access tokens -> Tokens (classic).

Click Generate new token (classic).

Give it a name (e.g., NuGet Publish Token).

Check the boxes for write:packages and read:packages. (Checking write:packages usually auto-checks repo too, which is fine).

Generate the token and copy it immediately (you will never see it again).



Tell your computer about GitHub Packages
dotnet nuget add source "https://nuget.pkg.github.com/YOUR_USERNAME/index.json" --name "github" --username "YOUR_USERNAME" --password "YOUR_PAT" --store-password-in-clear-text

delete obj, bin
dotnet clean
dotnet build --configuration Release
dotnet pack --configuration Release --force
dotnet nuget push ".\bin\Release\*.nupkg" --source "github" --api-key YOUR_PAT