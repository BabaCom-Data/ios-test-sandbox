platform :ios, '14.0'
use_frameworks!
project 'App/App.xcodeproj'

# Workaround for potential build_dir nil error
ENV['COCOAPODS_DISABLE_DETERMINISTIC_UUIDS'] = 'YES'
ENV['BUILD_DIR'] = 'build'

install! 'cocoapods',
  :disable_input_output_paths => true

def capacitor_pods
  pod 'Capacitor', :path => '../../node_modules/@capacitor/ios'
  pod 'CapacitorCordova', :path => '../../node_modules/@capacitor/ios'
  pod 'CapacitorCamera', :path => '../../node_modules/@capacitor/camera'
  pod 'CapacitorSplashScreen', :path => '../../node_modules/@capacitor/splash-screen'
end

target 'App' do
  capacitor_pods
end

post_install do |installer|
  assertDeploymentTarget(installer)

  installer.pods_project.build_configurations.each do |config|
    config.build_settings['BUILD_DIR'] ||= 'build'
    config.build_settings['CONFIGURATION_BUILD_DIR'] ||= 'build/$(CONFIGURATION)'
  end
end
