# load 'deploy' if respond_to?(:namespace) # cap2 differentiator
# Dir['vendor/plugins/*/recipes/*.rb'].each { |plugin| load(plugin) }
# load 'config/deploy'

load 'deploy' if respond_to?(:namespace) # cap2 differentiator

default_run_options[:pty] = true

# be sure to change these
set :user, 'jacob'
set :domain, '67.23.0.192'
set :application, 'fu2008'

# the rest should be good
# set :repository,  "#{user}@#{domain}:git/#{application}.git" 
set :repository,  "git@github.com:jacobpatton/#{application}.git"
set :deploy_to, "/var/www/#{application}" 
set :deploy_via, :remote_cache
set :scm, 'git'
set :branch, 'master'
# set :git_shallow_clone, 1
set :scm_verbose, true
# set :scm_username, 'lachlanhardy'
set :use_sudo, false
set :group, "deploy"
set :ssh_options, { :forward_agent => true } # this is so we don't need a appdeploy key

server domain, :app, :web

namespace :deploy do
  task :restart do
    run "touch #{current_path}/tmp/restart.txt" 
  end
  
  web.task :disable, :roles => :web do
    run "cp #{current_path}/public/maintenance.html  #{shared_path}/system/maintenance.html"
  end
  
end