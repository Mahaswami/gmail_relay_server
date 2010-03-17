
require 'fileutils'
include FileUtils

task :default => :package do

end
desc "Package Relay Server for deployment"
task :package do
  `ant`
  Dir.chdir("../mailster_smtp") do
    `ant`
  end
  rm_r "package" rescue nil
  mkdir "package"
  `svn export bin package/bin`
  mkdir "package/lib"
  cp "dist/GmailRelayServer.jar", "package/lib"
  cp_r "dist/lib", "package"
  cp "../mailster_smtp/dist/MailsterSMTP.jar", "package/lib"
  cp_r "../mailster_smtp/dist/lib", "package"
  #mkdir "package/lib"

end

