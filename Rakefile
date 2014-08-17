require 'rspec/core/rake_task'

RSpec::Core::RakeTask.new(:spec)

begin
  require 'foodcritic'

  FoodCritic::Rake::LintTask.new do |task|
    task.options = { :fail_tags => [ 'any' ] }
  end

  task :default => [ :foodcritic, :spec ]
rescue LoadError
  task :default => [ :spec ]
end

begin
  require 'kitchen/rake_tasks'
  Kitchen::RakeTasks.new
rescue LoadError
  puts ">>>>> Kitchen gem not loaded, omitting tasks" unless ENV['CI']
end
