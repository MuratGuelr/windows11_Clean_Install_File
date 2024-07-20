# [ConsolAktif YouTube](https://www.youtube.com/consolaktif)

# Windows Ayarları

## Maximum Password Age Ayarı

Her 42 günde bir parolanızı değiştirmeniz gerekmiyor.

```sh
net.exe accounts /maxpwage:UNLIMITED
```

## Hibernation Özelliği

Laptop kullanıyorsanız açık bırakabilirsiniz. (Bilgisayarınız daha hızlı açılır/kapanır, ancak batarya ömrü kısalabilir.)

```sh
reg.exe add "HKLM\System\CurrentControlSet\Control\Session Manager\Power" /v HibernateEnabled /t REG_DWORD /d 0 /f
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FlyoutMenuSettings" /v ShowHibernateOption /t REG_DWORD /d 0 /f
```

## Windows Update Ayarı

Windows Update'i sadece Microsoft sunucularından indirecek.

```sh
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DeliveryOptimization\Config" /v DODownloadMode /t REG_DWORD /d 0 /f
```

## Driver Arama Ayarı

Windows driverları dosyalarınızda aramak yerine ilk olarak Windows Update ile arar.

```sh
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DriverSearching" /v SearchOrderConfig /t REG_DWORD /d 1 /f
```

## Multimedya Uygulamaları için Öncelik Ayarı

Sistem kaynaklarını oyunlar ve edit yazılımlarına öncelik verir.

```sh
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile" /v SystemResponsiveness /t REG_DWORD /d 0 /f
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile" /v NetworkThrottlingIndex /t REG_DWORD /d 4294967295 /f
```

## Sayfa Dosyası Ayarı

Kapanışta sanal bellek için oluşturulan page file dosyasını silmez.

```sh
reg.exe add "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management" /v ClearPageFileAtShutdown /t REG_DWORD /d 0 /f
```

## Grafik Kartları İçin Öncelik Ayarı

Grafik kartlarına oyunlar için daha yüksek öncelik verir.

```sh
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile\Tasks\Games" /v "GPU Priority" /t REG_DWORD /d 8 /f
```

## CPU İçin Öncelik Ayarı

CPU'ya oyunlar için daha yüksek öncelik verir.

```sh
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile\Tasks\Games" /v Priority /t REG_DWORD /d 6 /f
```

## Zamanlama Önceliği Ayarı

Oyunların sistemin zamanlamasında daha yüksek bir önceliğe sahip olmasını sağlar.

```sh
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile\Tasks\Games" /v "Scheduling Category" /t REG_SZ /d "High" /f
```

## Wifi Sense Özelliği

Otomatik olarak etrafta bağlanılabilecek wifi aramasını ve bağlanmasını engeller.

```sh
reg.exe add "HKLM\Software\Microsoft\PolicyManager\default\WiFi\AllowWiFiHotSpotReporting" /v Value /t REG_DWORD /d 0 /f
reg.exe add "HKLM\Software\Microsoft\PolicyManager\default\WiFi\AllowAutoConnectToWiFiSenseHotspots" /v Value /t REG_DWORD /d 0 /f
```

## Xbox Game Bar Ayarı

Xbox Game bar'ı kapatır.

```sh
reg.exe add "HKLM\SOFTWARE\Policies\Microsoft\Windows\GameDVR" /v AllowGameDVR /t REG_DWORD /d 0 /f
```

## Push To Install Özelliği

Uygulamaların otomatik olarak Microsoft Store veya servislerden uygulama indirip bilgisayarınıza yüklemesine izin vermez.

```sh
reg.exe add "HKLM\SOFTWARE\Policies\Microsoft\PushToInstall" /v "DisablePushToInstall" /t REG_DWORD /d 1 /f
```

## Özelleştirilmiş Reklamlar

Özelleştirilmiş reklamları, uygulama önerilerini, reklamları ve ipuçlarını devre dışı bırakır.

```sh
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Notepad" /v ShowStoreBanner /t REG_DWORD /d 0 /f
```

## Görev Çubuğu Ayarı

Görev çubuğunu sol tarafaya yaslar aynı Windows 10'daki gibi.

```sh
reg.exe add "HKU\DefaultUser\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v TaskbarAl /t REG_DWORD /d 0 /f
```

## Arama İkonu

Görev çubuğundaki arama ikonunu gizler.

```sh
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Search" /v SearchboxTaskbarMode /t REG_DWORD /d 0 /f
```

## Başlat Menüsü

Yeni eklenen uygulamaların ve önerilerin başlat menüsünden gözükmesini engeller.

```sh
reg.exe add "HKU\DefaultUser\Software\Policies\Microsoft\Windows\Explorer" /v HideRecentlyAddedApps /t REG_DWORD /d 1 /f
reg.exe add "HKU\DefaultUser\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v Start_IrisRecommendations /t REG_DWORD /d 0 /f
```

## Arka Plan Uygulamaları

Uygulamaların arkada işlem yapmasına izin vermez. Ancak bazı uygulamarın çalışmasını etkileyebilir.

```sh
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\BackgroundAccessApplications" /v GlobalUserDisabled /t REG_DWORD /d 1 /f
```

## Dosya Gezgini

Dosya gezginini açtığınızda daha önceden kullanmış olduğunuz dosyaları yukarıda göstermek yerine sadece "Bilgisayarım'ı" gösterir.

```sh
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v LaunchTo /t REG_DWORD /d 1 /f
```

## Görsel Efektler

Görsel efektleri performans ayarına getiriyor.

```sh
reg.exe add "HKU\DefaultUser\Control Panel\Desktop" /v MenuShowDelay /t REG_DWORD /d 1 /f
```

## Mouse Ayarı

Fare imlecinin bir öğe üzerinde sabit kalması gereken süreyi (milisaniye cinsinden) belirler. Normal değeri 400.

```sh
reg.exe add "HKU\DefaultUser\Control Panel\Mouse" /v MouseHoverTime /t REG_SZ /d "400" /f
```

## Klasik Sağ Tık Menüsü

Windows 11 için Windows 10'daki sağ tık menüsünü geri getirir.

```sh
reg.exe add "HKU\DefaultUser\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /ve /t REG_SZ /d "" /f
```

## Mouse Hız Ayarı

Mouse ayarlarındaki işaretçi hassasiyetini arttır ayarını devre dışı bırakır.

```sh
reg.exe add "HKU\DefaultUser\Control Panel\Mouse" /v MouseSpeed /t REG_SZ /d "0" /f
reg.exe add "HKU\DefaultUser\Control Panel\Mouse" /v MouseThreshold1 /t REG_SZ /d "0" /f
reg.exe add "HKU\DefaultUser\Control Panel\Mouse" /v MouseThreshold2 /t REG_SZ /d "0" /f
```

## Yapışkan Tuşlar

Yapışkan tuşları kapatır. (Sürekli shifte basıldığında açılan yapışkan tuşlar.)

```sh
reg.exe add "HKU\DefaultUser\Control Panel\Accessibility\StickyKeys" /v Flags /t REG_SZ /d "506" /f
reg.exe add "HKU\DefaultUser\Control Panel\Accessibility\StickyKeys" /v HotkeyFlags /t REG_SZ /d "58" /f
```

## Snap Assist

Windows da bir uygulamayı sağ sola yukarı götürdüğünüzde sağa sola veya bütün ekranı kaplamasını ve ona göre düzenlemesi özelliğini devre dışı bırakır.

```sh
reg.exe add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v SnapAssist /t REG_DWORD /d 0 /f
```

## Arama

Dosyaları ve klasörleri başlat menüsünden veya görev çubuğundaki arama ikonundan aramayı kapatır.

```sh
reg.exe add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Search" /v SearchboxTaskbarMode /t REG_DWORD /d 0 /f
```

## Game Bar Ayarı

Oyunlarda anlık klip kaydı yapmayı kapatır.

```sh
reg.exe add "HKEY_CURRENT_USER\System\GameConfigStore" /v GameDVR_Enabled /t REG_DWORD /d 0 /f
```

## Microsoft Edge

Microsoft Edge'de açılış sayfasını ve yeni sekme sayfasını boş yapar.

```sh
reg.exe add "HKEY_CURRENT_USER\Software\Microsoft\Edge\Main" /v Start Page /t REG_SZ /d "" /f
reg.exe add "HKEY_CURRENT_USER\Software\Microsoft\Edge\Main" /v NewTabPage /t REG_SZ /d "" /f
```

## .NET Framework 3.5'i Açma

.NET Framework 3.5'i etkinleştirir.

```sh
DISM /Online /Enable-Feature /FeatureName:NetFx3 /All /Source:X:\sources\sxs /LimitAccess
```

## Microsoft Teams ve OneDrive'ı Silme

Microsoft Teams ve OneDrive'ı kaldırır.

```sh
# Removes OneDrive
Remove-Item "C:\Users\Default\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\OneDrive.lnk" -ErrorAction Continue
Remove-Item "C:\Users\Default\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\OneDrive.exe" -ErrorAction Continue
Remove-Item "C:\Windows\System32\OneDriveSetup.exe" -ErrorAction Continue
Remove-Item "C:\Windows\SysWOW64\OneDriveSetup.exe" -ErrorAction Continue

# Removes Microsoft Teams
$TeamsPath = [System.IO.Path]::Combine($env:LOCALAPPDATA, 'Microsoft', 'Teams')
$TeamsUpdateExePath = [System.IO.Path]::Combine($TeamsPath, 'Update.exe')
```

## Telemetry'yi Devre Dışı Bırakma

Windows'a veri gönderen hizmetleri devre dışı bırakır.

```sh
# Disable Scheduled Tasks
$scheduledTasks = @(
    "Microsoft\Windows\Application Experience\Microsoft Compatibility Appraiser",
    "Microsoft\Windows\Application Experience\ProgramDataUpdater",
    "Microsoft\Windows\Autochk\Proxy",
    "Microsoft\Windows\Customer Experience Improvement Program\Consolidator",
    "Microsoft\Windows\Customer Experience Improvement Program\UsbCeip",
    "Microsoft\Windows\DiskDiagnostic\Microsoft-Windows-DiskDiagnosticDataCollector",
    "Microsoft\Windows\Feedback\Siuf\DmClient",
    "Microsoft\Windows\Feedback\Siuf\DmClientOnScenarioDownload",
    "Microsoft\Windows\Windows Error Reporting\QueueReporting",
    "Microsoft\Windows\Application Experience\MareBackup",
    "Microsoft\Windows\Application Experience\StartupAppTask",
    "Microsoft\Windows\Application Experience\PcaPatchDbTask",
    "Microsoft\Windows\Maps\MapsUpdateTask"
)
foreach ($task in $scheduledTasks) {
    schtasks /Change /TN $task /Disable
}
```

## Nihai Performans Ayarını Açma

Windows'da gizli olarak bulunan Nihai Performans ayarını açar ve uygular.

```sh
# Enable the Ultimate Performance power plan
powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61

# Set the Ultimate Performance power plan as active
powercfg -setactive e9a42b02-d5df-448d-aa00-03f14749eb61
```

## Gereksiz Servisleri Elle Başlatma

Gereksiz servisleri elle başlatmaya alır.

```sh
# Set Services to Manual
Write-Output 'Set Services to Manual: Turns a bunch of system services to manual that do not need to be running all the time.'
Set-Service -Name 'AJRouter' -StartupType Disabled -ErrorAction Continue
Set-Service -Name 'ALG' -StartupType Manual -ErrorAction Continue
Set-Service -Name 'AppIDSvc' -StartupType Manual -ErrorAction Continue
Set-Service -Name 'AppMgmt' -StartupType Manual -ErrorAction Continue
Set-Service -Name 'AppReadiness' -StartupType Manual -ErrorAction Continue
```

## Windows Hesabı ile Giriş Kısmını Geçme

Windows kurulumunda Windows hesabı ile giriş kısmını geçer.

```sh
:: Bypasses Microsoft Account Creation
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\OOBE" /v BypassNRO /t REG_DWORD /d 1 /f
```

## Dev Home & Yeni Outlook ve Chat Auto'nun Yüklenmesini Önleme

Dev Home, Yeni Outlook ve Chat Auto'nun yüklenmesini önler.

```sh
:: Prevents Dev Home Installation
reg.exe delete "HKLM\SOFTWARE\Microsoft\WindowsUpdate\Orchestrator\UScheduler_Oobe\DevHomeUpdate" /f

:: Prevents New Outlook for Windows Installation
reg.exe delete "HKLM\SOFTWARE\Microsoft\WindowsUpdate\Orchestrator\UScheduler_Oobe\OutlookUpdate" /f

:: Prevents Chat Auto Installation and Removes Chat Icon
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Communications" /v ConfigureChatAutoInstall /t REG_DWORD /d 0 /f
reg.exe add "HKLM\SOFTWARE\Policies\Microsoft\Windows\Windows Chat" /v "ChatIcon" /t REG_DWORD /d 3 /f
```

## Başlat Menüsünü Boş Olarak Ayarlama

Başlat menüsünü boş olarak ayarlar.

```sh
:: Start Menu Customization
reg.exe add "HKLM\SOFTWARE\Microsoft\PolicyManager\current\device\Start" /v ConfigureStartPins /t REG_SZ /d "{ \"pinnedList\": [] }" /f
reg.exe add "HKLM\SOFTWARE\Microsoft\PolicyManager\current\device\Start" /v ConfigureStartPins_ProviderSet /t REG_DWORD /d 1 /f
reg.exe add "HKLM\SOFTWARE\Microsoft\PolicyManager\current\device\Start" /v ConfigureStartPins_WinningProvider /t REG_SZ /d B5292708-1619-419B-9923-E5D9F3925E71 /f
reg.exe add "HKLM\SOFTWARE\Microsoft\PolicyManager\providers\B5292708-1619-419B-9923-E5D9F3925E71\default\Device\Start" /v ConfigureStartPins /t REG_SZ /d "{ \"pinnedList\": [] }" /f
reg.exe add "HKLM\SOFTWARE\Microsoft\PolicyManager\providers\B5292708-1619-419B-9923-E5D9F3925E71\default\Device\Start" /v ConfigureStartPins_LastWrite /t REG_DWORD /d 1 /f
```

## Haber ve İlgini Çekebilecekler Kısmını Kaldırma

Haber ve ilgini çekebilecekler kısmını kaldırır.

```sh
:: Disables News and Interests
reg.exe add "HKLM\SOFTWARE\Policies\Microsoft\Dsh" /v AllowNewsAndInterests /t REG_DWORD /d 0 /f
```

## Uygulama Promosyonlarını Kaldırma

Windows'un sürekli önermeye ve satmaya çalıştığı uygulama promosyonlarını kaldırır.

```sh
:: Disables Windows Consumer Features Like App Promotions etc.
reg.exe add "HKLM\Software\Policies\Microsoft\Windows\CloudContent" /v "DisableWindowsConsumerFeatures" /t REG_DWORD /d 0 /f
```

## Otomatik Bitlocker Dosya Şifrelemesini Devre Dışı Bırakma

Otomatik Bitlocker dosya şifrelemesini devre dışı bırakır.

```sh
:: Disables Bitlocker Auto Encryption on Windows 11 24H2 and Onwards
reg.exe add "HKLM\SYSTEM\CurrentControlSet\Control\BitLocker" /v "PreventDeviceEncryption" /t REG_DWORD /d 1 /f
reg.exe add "HKLM\SOFTWARE\Policies\Microsoft\Windows\EnhancedStorageDevices" /v TCGSecurityActivationDisabled /t REG_DWORD /d 1 /f
```

## Windows Güncellemelerini Yalnızca Güvenlik Güncellemeleri ile Sınırlama

Sadece Windows güvenlik güncellemelerini yükler ve diğer güncellemeleri de 2 yıl geciktirir.

```sh
:: Sets Windows Update to Only Install Security Updates and Delay Other Updates for 2 Years
reg.exe add "HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU" /v AUOptions /t REG_DWORD /d 3 /f
reg.exe add "HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate" /v DeferFeatureUpdates /t REG_DWORD /d 1 /f
reg.exe add "HKLM\SOFTWARE\Policies
```

```markdown
xe add "HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate" /v DeferFeatureUpdatesPeriodInDays /t REG_DWORD /d 365 /f
reg.exe add "HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate" /v DeferQualityUpdates /t REG_DWORD /d 1 /f
reg.exe add "HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate" /v DeferQualityUpdatesPeriodInDays /t REG_DWORD /d 365 /f
```

## Cortana'yı Devre Dışı Bırakma

Cortana'yı devre dışı bırakır.

```sh
:: Disables Cortana
reg.exe add "HKLM\Software\Policies\Microsoft\Windows\Windows Search" /v AllowCortana /t REG_DWORD /d 0 /f
```

## Aktivite Geçmişini Devre Dışı Bırakma

Bilgisayarınızda yaptıklarınızı Windows'a göndermeyi devre dışı bırakır.

```sh
:: Disables Activity History
reg.exe add "HKLM\SOFTWARE\Policies\Microsoft\Windows\System" /v EnableActivityFeed /t REG_DWORD /d 0 /f
reg.exe add "HKLM\SOFTWARE\Policies\Microsoft\Windows\System" /v PublishUserActivities /t REG_DWORD /d 0 /f
reg.exe add "HKLM\SOFTWARE\Policies\Microsoft\Windows\System" /v UploadUserActivities /t REG_DWORD /d 0 /f
```

## Konum Takibini Devre Dışı Bırakma

Konum bilginizi Windows'a göndermeyi devre dışı bırakır.

```sh
:: Disables Location Tracking
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\CapabilityAccessManager\ConsentStore\location" /v Value /t REG_SZ /d Deny /f
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Sensor\Overrides\{BFA794E4-F964-4FDB-90F6-51056BFE4B44}" /v SensorPermissionState /t REG_DWORD /d 0 /f
reg.exe add "HKLM\SYSTEM\CurrentControlSet\Services\lfsvc\Service\Configuration" /v Status /t REG_DWORD /d 0 /f
reg.exe add "HKLM\SYSTEM\Maps" /v AutoUpdateEnabled /t REG_DWORD /d 0 /f
```

## Telemetry'yi Devre Dışı Bırakma

Windows'un veri toplamasını önler.

```sh
:: Disables Telemetry
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection" /v AllowTelemetry /t REG_DWORD /d 0 /f
reg.exe add "HKLM\SOFTWARE\Policies\Microsoft\Windows\DataCollection" /v AllowTelemetry /t REG_DWORD /d 0 /f
```

## Delivery Optimization'ı Devre Dışı Bırakma

Microsoft Store uygulamasının arkada veri akışı sağlamasına izin verilmez.

```sh
:: Disables Delivery Optimization
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DeliveryOptimization\Config" /v DODownloadMode /t REG_DWORD /d 0 /f
```

## Driver Arama Ayarı

Yüklemek istediğiniz driverlar için ilk olarak Windows Update kullanılır.

```sh
:: Search Windows Update for Drivers First
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DriverSearching" /v SearchOrderConfig /t REG_DWORD /d 1 /f
```

## Multimedya Uygulamaları için Öncelik Ayarı

Oyunlar ve edit uygulamaları gibi yüksek güç gerektiren uygulamalara yüksek öncelik verir.

```sh
:: Gives Multimedia Applications like Games and Video Editing a Higher Priority
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile" /v SystemResponsiveness /t REG_DWORD /d 0 /f
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile" /v NetworkThrottlingIndex /t REG_DWORD /d 4294967295 /f
```

## Page File Ayarı

Page file dosyasının Windows kapanırken silinip silinmediğini kontrol eder. Sadece bunun hakkında videom var. [ConsolAktif Videosu](https://www.youtube.com/watch?v=9pXwFi7BF18)

```sh
:: Controls whether the memory page file is cleared at shutdown. Value 0 means it will not be cleared, speeding up shutdown.
reg.exe add "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Memory Management" /v ClearPageFileAtShutdown /t REG_DWORD /d 0 /f
```

## IRP Yığın Boyutunu Artırma

Windows işletim sisteminde ağ performansını ve kararlılığını artırmak için IRP (I/O Request Packet) yığın boyutunu artırır.

```sh
:: Increases IRP stack size to 30 for the LanmanServer service to Improve Network Performance and Stability
reg.exe add "HKLM\SYSTEM\CurrentControlSet\Services\LanmanServer\Parameters" /v IRPStackSize /t REG_DWORD /d 30 /f
```

## Meet Now'ı Görev Çubuğundan Kaldırma

Meet Now'ı görev çubuğundan kaldırır.

```sh
:: Hides the Meet Now Button on the Taskbar
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\Explorer" /v HideSCAMeetNow /t REG_DWORD /d 1 /f
```

## Grafik Kartları İçin Öncelik Ayarı

Ekran kartını oyunlar için yüksek önceliğe ayarlar.

```sh
:: Gives Graphics Cards a Higher Priority for Gaming
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile\Tasks\Games" /v "GPU Priority" /t REG_DWORD /d 8 /f

:: Gives the CPU a Higher Priority for Gaming
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile\Tasks\Games" /v Priority /t REG_DWORD /d 6 /f

:: Gives Games a higher priority in the system's scheduling
reg.exe add "HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile\Tasks\Games" /v "Scheduling Category" /t REG_SZ /d "High" /f
```

## Microsoft Edge'de "Kuruluşunuz Tarafından Yönetiliyor" Mesajını Kaldırma

Microsoft Edge tarayıcısında "Kuruluşunuz tarafından yönetiliyor" mesajını kaldırır.

```sh
:: Fix Managed by your organization in Edge
reg.exe delete "HKLM\SOFTWARE\Policies\Microsoft\Edge" /f
```

## Wifi Sense Özelliğini Devre Dışı Bırakma

Windows'un sürekli etrafta bağlanılabilecek wifi ağı aramasını engeller. (Bu ayar normal wifi aramasını etkilemez.)

```sh
:: Set Registry Keys to Disable Wifi-Sense
reg.exe add "HKLM\Software\Microsoft\PolicyManager\default\WiFi\AllowWiFiHotSpotReporting" /v Value /t REG_DWORD /d 0 /f
reg.exe add "HKLM\Software\Microsoft\PolicyManager\default\WiFi\AllowAutoConnectToWiFiSenseHotspots" /v Value /t REG_DWORD /d 0 /f
```

## OneDrive'ın Otomatik Yedeklemesini Devre Dışı Bırakma

OneDrive'ın otomatik olarak dosyalarınızı kayıt etmesini önler.

```sh
:: Disables OneDrive Automatic Backups of Important Folders (Documents, Pictures etc.)
reg.exe add "HKLM\SOFTWARE\Policies\Microsoft\OneDrive" /v KFMBlockOptIn /t REG_DWORD /d 1 /f
reg.exe add "HKLM\SOFTWARE\Policies\Microsoft\Windows\OneDrive" /v DisableFileSyncNGSC /t REG_DWORD /d 1 /f
```

## Copilot'ı Kaldırma

Copilot'ı kaldırır.

```sh
:: Removes Copilot
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Runonce" /v "UninstallCopilot" /t REG_SZ /d "" /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Policies\Microsoft\Windows\WindowsCopilot" /v TurnOffWindowsCopilot /t REG_DWORD /d 1 /f
```

## Notepad Mağaza Banner'ını Kaldırma

Windows Notepad uygulamasında görünen mağaza banner'ını kaldırır.

```sh
:: Removes Store Banner in Notepad
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Notepad" /v ShowStoreBanner /t REG_DWORD /d 0 /f
```

## Arama İkonunu Gizleme

Arama ikonunu gizler.

```sh
:: Hides Search Icon on Taskbar
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Search" /v SearchboxTaskbarMode /t REG_DWORD /d 0 /f
```

## Yeni Eklenmiş Uygulamalar ve Önerileri Kaldırma

Yeni eklenmiş uygulamalar ve önerileri kaldırır.

```sh
:: Disables Recently Added Apps and Recommendations in the Start Menu
reg.exe add "HKU\DefaultUser\Software\Policies\Microsoft\Windows\Explorer" /v HideRecentlyAddedApps /t REG_DWORD /d 1 /f
reg.exe add "HKU\DefaultUser\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v Start_IrisRecommendations /t REG_DWORD /d 0 /f
```

## People Uygulamasını & Görev Görünümü Simgesini ve Haber ve İlginizi Çekebilecekler Kısmını Görev Çubuğundan Kaldırma

People uygulamasını & Görev Görünümü simgesini ve Haber ve ilgini çekebilecekler kısmını görev çubuğundan kaldırır.

```sh
:: Hides or Removes People from Taskbar
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Advanced\People" /v PeopleBand /t REG_DWORD /d 0 /f

:: Hides Task View Button on Taskbar
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ShowTaskViewButton /t REG_DWORD /d 0 /f

:: Hides and Removes News and Interests from PC and Taskbar
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Feeds" /v ShellFeedsTaskbarViewMode /t REG_DWORD /d 2 /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Feeds" /v ShellFeedsEnabled /t REG_DWORD /d 0 /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Policies\Microsoft\Windows\Windows Feeds" /v EnableFeeds /t REG_DWORD /d 0 /f
```

## Bildirimleri Kapatma

Bildirimleri kapatır. (Eğer bildirimler sizin için önemli ise bu kodu kaldırabilirsiniz.)

```sh
:: Hides or Removes Notifications
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\PushNotifications" /v ToastEnabled /t REG_DWORD /d 0 /f
```

## Telemetry ve Reklamları Devre Dışı Bırakma

Windows veri toplama ve reklamlarını devre dışı bırakır.

```sh
:: Disables Telemetry and Ads
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Siuf\Rules" /v NumberOfSIUFInPeriod /t REG_DWORD /d 0 /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Policies\Microsoft\Windows\CloudContent" /v DisableTailoredExperiencesWithDiagnosticData /t REG_DWORD /d 1 /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Policies\Microsoft\Windows\CloudContent" /v DisableWindowsConsumerFeatures /t REG_DWORD /d 1 /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ShowSyncProviderNotifications /t REG_DWORD /d 0 /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\AdvertisingInfo" /v Enabled /t REG_DWORD /d 0 /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\InputPersonalization\TrainedDataStore" /v "HarvestContacts" /t REG_DWORD /d 0 /f
```

## Dosya Gezgini Ayarı

Dosya gezginini açtığınızda "Home" kısmı yerine "Bu Bilgisayar" açılır.

```sh
:: Set File Explorer to Open This PC instead of Quick Access
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v LaunchTo /t REG_DWORD /d 1 /f
```

## Otomatik Uygulama Kapatma

Bilgisayarı kapata tıkladığınızda arkadaki bütün uygulamalar otomatik olarak kapatılır.

```sh
:: On Shutdown, Windows will automatically close any running applications
reg.exe add "HKU\DefaultUser\Control Panel\Desktop" /v AutoEndTasks /t REG_DWORD /d 1 /f
```

## Mouse Hover Süresini Ayarlama

Mouse'un dosyaların üzerine geldiğindeki algılama süresini 200 milisaniyeye indirir. Normal değer 400'dür ve kodda da normalde 400'dü yani varsayılan değer. (Ben 200 yaptım. Önerilen ayar 200'dür.)

```sh
:: Sets the Mouse hover time to 200 milliseconds
reg.exe add "HKU\DefaultUser\Control Panel\Mouse" /v MouseHoverTime /t REG_SZ /d "200" /f
```

## Görsel Efektler Ayarı

Normal kod sistemi performans ayarına alıyor ancak bu şekilde hem daha iyi gözüküyor hem de daha iyi performans alınıyor.

```sh
:: Set Display for Performance
reg.exe add "HKU\DefaultUser\Control Panel\Desktop" /v DragFullWindows /t REG_SZ /d 1 /f
reg.exe add "HKU\DefaultUser\Control Panel\Desktop" /v MenuShowDelay /t REG_SZ /d 200 /f
reg.exe add "HKU\DefaultUser\Control Panel\Desktop\WindowMetrics" /v MinAnimate /t REG_SZ /d 0 /f
reg.exe add "HKU\DefaultUser\Control Panel\Keyboard" /v KeyboardDelay /t REG_DWORD /d 0 /f
reg.exe add "HKU\DefaultUser\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ListviewAlphaSelect /t REG_DWORD /d 1 /f
reg.exe add "HKU\DefaultUser\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ListviewShadow /t REG_DWORD /d 0 /f
reg.exe add "HKU\DefaultUser\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v TaskbarAnimations /t REG_DWORD /d 0 /f
reg.exe add "HKU\DefaultUser\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v TaskbarMn /t REG_DWORD /d 0 /f
reg.exe add "HKU\DefaultUser\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v TaskbarDa /t REG_DWORD /d 0 /f
reg.exe add "HKU\DefaultUser\Software\Microsoft\Windows\CurrentVersion\Explorer\VisualEffects" /v VisualFXSetting /t REG_DWORD /d 3 /f
reg.exe add "HKU\DefaultUser\Software\Microsoft\Windows\DWM" /v EnableAeroPeek /t REG_DWORD /d 0 /f
```

## Klasik Sağ Tık Menüsü

Windows 11'in sağ tıklama menüsünü Windows 10'a döndürüyor. (2 kere tıklamak zorunda kalmıyorsunuz.)

```sh
:: Set Classic Right-Click Menu for Windows 11
reg.exe add "HKU\DefaultUser\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /ve /t REG_SZ /d "" /f
```

## NumLock'u Başlangıçta Açma

Bilgisayar başlarken numlock otomatik açılıyor.

```sh
:: Enables NumLock on Startup
reg.exe add "HKU\DefaultUser\Control Panel\Keyboard" /v InitialKeyboardIndicators /t REG_SZ /d 2 /f
```

## Yapışkan Tuşları Devre Dışı Bırakma

Yapışkan tuşları devre dışı bırakır.

```sh
:: Disables Sticky Keys
reg.exe add "HKU\DefaultUser\Control Panel\Accessibility\StickyKeys" /v Flags /t REG_SZ /d "506" /f
reg.exe add "HKU\DefaultUser\Control Panel\Accessibility\StickyKeys" /v HotkeyFlags /t REG_SZ /d "58" /f
```

## Dosya Uzantılarını Gösterme

Dosya uzantılarını açar. (Normalde göremediğiniz .exe, .pdf, .iss gibi)

```sh
:: Enables Show File Extensions
reg.exe add "HKU\DefaultUser\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v HideFileExt /t REG_DWORD /d 0 /f
```

## Koyu Modu Açma

Koyu modu açar. (Eğer koyu mod istemiyorsanız bu kodu da silebilirsiniz.)

```sh
:: Enables Dark Mode
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows
```

```markdown
ser\SOFTWARE\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v AppsUseLightTheme /t REG_DWORD /d 0 /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v ColorPrevalence /t REG_DWORD /d 0 /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v EnableTransparency /t REG_DWORD /d 1 /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v SystemUsesLightTheme /t REG_DWORD /d 0 /f
```

## Windows Eski Fotoğraf Görüntüleyicisini Geri Getirme

Windows'un eski fotoğraf görüntüleyicini Windows'un varsayılan fotoğraf görüntüleyicisi yapar. (Ben bu fotoğraf görüntüleyicisini çok çağ dışı kaldığı için bu kodları sildim.)

```sh
:: Restore Windows Photo Viewer and Set as Default Program for Image Files
:: Restore Windows Photo Viewer
reg.exe add "HKU\DefaultUser\SOFTWARE\Classes\.bmp" /ve /d "PhotoViewer.FileAssoc.Tiff" /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Classes\.cr2" /ve /d "PhotoViewer.FileAssoc.Tiff" /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Classes\.dib" /ve /d "PhotoViewer.FileAssoc.Tiff" /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Classes\.gif" /ve /d "PhotoViewer.FileAssoc.Tiff" /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Classes\.ico" /ve /d "PhotoViewer.FileAssoc.Tiff" /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Classes\.jfif" /ve /d "PhotoViewer.FileAssoc.Tiff" /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Classes\.jpe" /ve /d "PhotoViewer.FileAssoc.Tiff" /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Classes\.jpeg" /ve /d "PhotoViewer.FileAssoc.Tiff" /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Classes\.jpg" /ve /d "PhotoViewer.FileAssoc.Tiff" /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Classes\.jxr" /ve /d "PhotoViewer.FileAssoc.Tiff" /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Classes\.png" /ve /d "PhotoViewer.FileAssoc.Tiff" /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Classes\.tif" /ve /d "PhotoViewer.FileAssoc.Tiff" /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Classes\.tiff" /ve /d "PhotoViewer.FileAssoc.Tiff" /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Classes\.wdp" /ve /d "PhotoViewer.FileAssoc.Tiff" /f

:: Create Relevant File Associations
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.bmp\OpenWithProgids" /v "PhotoViewer.FileAssoc.Tiff" /t REG_NONE /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.cr2\OpenWithProgids" /v "PhotoViewer.FileAssoc.Tiff" /t REG_NONE /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.dib\OpenWithProgids" /v "PhotoViewer.FileAssoc.Tiff" /t REG_NONE /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.gif\OpenWithProgids" /v "PhotoViewer.FileAssoc.Tiff" /t REG_NONE /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.ico\OpenWithProgids" /v "PhotoViewer.FileAssoc.Tiff" /t REG_NONE /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.jfif\OpenWithProgids" /v "PhotoViewer.FileAssoc.Tiff" /t REG_NONE /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.jpe\OpenWithProgids" /v "PhotoViewer.FileAssoc.Tiff" /t REG_NONE /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.jpeg\OpenWithProgids" /v "PhotoViewer.FileAssoc.Tiff" /t REG_NONE /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.jpg\OpenWithProgids" /v "PhotoViewer.FileAssoc.Tiff" /t REG_NONE /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.jxr\OpenWithProgids" /v "PhotoViewer.FileAssoc.Tiff" /t REG_NONE /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.png\OpenWithProgids" /v "PhotoViewer.FileAssoc.Tiff" /t REG_NONE /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.tif\OpenWithProgids" /v "PhotoViewer.FileAssoc.Tiff" /t REG_NONE /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.tiff\OpenWithProgids" /v "PhotoViewer.FileAssoc.Tiff" /t REG_NONE /f
reg.exe add "HKU\DefaultUser\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\FileExts\.wdp\OpenWithProgids" /v "PhotoViewer.FileAssoc.Tiff" /t REG_NONE /f
```

## Ayarların açıklamaları genel olarak bu şekilde olacaktır.
