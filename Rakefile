require 'cucumber/rake/task'



  Cucumber::Rake::Task.new(:api, 'API tests') do |t|
    t.profile = 'api'
  end

  Cucumber::Rake::Task.new(:selenium, 'Selenium tests') do |t|
    t.profile = 'selenium'
  end

  Cucumber::Rake::Task.new(:touch, 'Touch tests') do |t|
    t.profile = 'touch'
  end


  desc "iPhone tests"
  task :iphone do
    
    ENV['IPHONE_SYM_PATH'] = "iWebDriver.app"

    Cucumber::Rake::Task.new(:iphone_runner) do |t|
      t.profile = 'iphone'
    end

    Rake::Task[:iphone_runner].invoke

  end

  desc "Sauce tests"
  task :sauce do
    unless ENV['SAUCE_USERNAME'] and ENV['SAUCE_KEY']
      puts "\n\nCan't run sauce tests without a sauce account"
      puts "You can get a free account here: http://saucelabs.com/"

      puts "Provide username and API Key: "
      puts "export SAUCE_USERNAME=username"
      puts "export SAUCE_KEY=api_key\n\n"
      puts "Skipping Sauce...\n\n"
    end

    Cucumber::Rake::Task.new(:sauce_runner) do |t|
      t.profile = 'sauce'
    end

    Rake::Task[:sauce_runner].invoke
  end


  desc "Run all tests"
  task :all => [:api, :selenium, :touch, :iphone, :sauce]

  task :default => :all
