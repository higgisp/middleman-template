desc "builds the site and uses rsync to deploy the site to the server"
task :deploy do
  require 'yaml'
  config = YAML::load_file("config.yml")["deploy"]
  host = config["host"]
  path = config["path"]
  user = config["user"]
  port = config["port"]
  cmd = <<-CMD
    middleman build
    cd build
    rsync -rRzPL --rsh="ssh -p 30000" . #{user}@#{host}:#{path}
  CMD
  exec(cmd)
end
task :d => :deploy

desc 'builds the site'
task :build do
  exec('middleman build')
end
task :b => :build

desc 'starts the middleman server'
task :server do
  exec('middleman')
end
task :s => :server
