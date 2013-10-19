source 'https://rubygems.org'

group :active_record do
  platforms :jruby do
    case ENV['CI_DB_ADAPTER']
    when 'mysql'
      gem 'activerecord-jdbcmysql-adapter', '>= 1.2'
      gem 'jdbc-mysql', '>= 5.1'
    when 'postgresql'
      gem 'activerecord-jdbcpostgresql-adapter', '>= 1.2'
      gem 'jdbc-postgres', '>= 9.2'
    else
      gem 'activerecord-jdbcsqlite3-adapter', '>= 1.3.0.beta1'
      gem 'jdbc-sqlite3', '>= 3.7'
    end
  end

  platforms :ruby, :mswin, :mingw do
    case ENV['CI_DB_ADAPTER']
    when 'mysql2'
      gem 'mysql2', '~> 0.3.11'
    when 'postgresql'
      gem 'pg', '>= 0.14'
    else
      gem 'sqlite3', '>= 1.3'
    end
  end
end

group :mongoid do
  # https://github.com/ahoward/mongoid-grid_fs/pull/31
  # mongoid commit cc7a0e709066aff444bc21cd9826e1568603934d broke
  # mongoid-grid_fs so we're pinning it to the commit before that.  we
  # can un-pin mongoid when mongoid-grid_fs becomes compatible with
  # mongoid master.
  gem 'mongoid', github: 'mongoid/mongoid', ref: '484aa0721e'
  gem 'mongoid-paperclip', '>= 0.0.8', :require => 'mongoid_paperclip'
  gem 'mongoid-grid_fs', github: 'ahoward/mongoid-grid_fs'
  gem 'carrierwave-mongoid', github: 'jnicklas/carrierwave-mongoid', :require => 'carrierwave/mongoid'
end

group :development do
  gem 'pry', '>= 0.9'
  gem 'pry-debugger', '>= 0.2', :platforms => :mri_19
end

group :test do
  # we were getting strange behavior only in jruby with rspec-core
  # 2.14.6.  All of the tests would pass but the rake task would
  # return 1 and cause the Travis build to fail, for example
  # https://travis-ci.org/sferik/rails_admin/jobs/12765829.  On my
  # machine it failed intermittently but on Travis it was consistent.
  # 2.14.5 works consistently so for now we'll pin it to that version.
  gem 'rspec-core', '2.14.5'
  gem 'cancan', '>= 1.6'
  gem 'capybara', '~> 2.0'
  gem 'carrierwave', '>= 0.8'
  gem 'coveralls', :require => false
  gem 'database_cleaner', '~> 1.0.0' # https://github.com/bmabey/database_cleaner/issues/224
  gem 'devise', '~> 3.0.0.rc'
  gem 'dragonfly', '>= 0.9'
  gem 'rack-cache', :require => 'rack/cache'
  gem 'factory_girl', '>= 4.2'
  gem 'generator_spec', '>= 0.8'
  gem 'launchy', '>= 2.2'
  gem 'mini_magick', '>= 3.4'
  gem 'paperclip', '>= 3.4'
  gem 'poltergeist'
  gem 'rspec-rails', '>= 2.14'
  gem 'simplecov', :require => false
  gem 'timecop', '>= 0.5'
end

gemspec
