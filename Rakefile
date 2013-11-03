require 'date'
require 'rake'

desc "Create a new post"
task :new_post, :title do |t, args|
  title = args[:title]
  today = Date.today.strftime '%Y-%m-%d'
  dashed_title = title.split(' ').join('-')
  post_filename = "#{today}-#{dashed_title}.md"
  puts "Creating a new post: #{post_filename}"
  File.open("_posts/#{post_filename}", "w") do |f|
    f.write """---
layout: post
title: #{title}
cover:
cover_attribution:
---
    """
  end
end
