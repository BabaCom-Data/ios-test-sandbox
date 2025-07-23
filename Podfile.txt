platform :ios, '14.0'
use_frameworks!
project 'App/App.xcodeproj'

require_relative '../../node_modules/@capacitor/ios/scripts/pods_helpers'

install! 'cocoapods', :disable_input_output_paths => true

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
end
