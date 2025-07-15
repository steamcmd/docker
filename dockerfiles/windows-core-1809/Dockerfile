######## INSTALL ########

# Set the base image
FROM mcr.microsoft.com/windows/servercore:1809

# Set alternative shell
SHELL ["powershell"]

# Set environment variables
ENV POWERSHELL_TELEMETRY_OPTOUT=1
ENV HOME="c:\steamcmd"

# Create system user
RUN New-LocalUser -Name "steamcmd" -NoPassword -AccountNeverExpires -UserMayNotChangePassword | Set-LocalUser -PasswordNeverExpires $true

# Switch to user
USER steamcmd

# Create SteamCMD directory
RUN New-Item -ItemType Directory "c:\steamcmd"

# Set SteamCMD working directory
WORKDIR $HOME

# Download and unpack SteamCMD archive
RUN Invoke-WebRequest http://media.steampowered.com/installer/steamcmd.zip -O c:\steamcmd\steamcmd.zip; \
    Expand-Archive c:\steamcmd\steamcmd.zip -DestinationPath c:\steamcmd; \
    Remove-Item c:\steamcmd\steamcmd.zip

# Update SteamCMD
RUN c:\steamcmd\steamcmd.exe +quit; exit 0

# Set default command
ENTRYPOINT c:\steamcmd\steamcmd.exe
CMD +help +quit
