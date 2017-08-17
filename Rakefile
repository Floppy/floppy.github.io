require 'jekyll/test/tasks'
task default: "jekyll:check"

require 'colorize'
namespace :generate do

  desc "Generate category pages from posts"
  task :categories do
    categories = Dir.glob("_posts/*").map do |file|
      frontmatter = YAML.load_file(file)
      frontmatter['categories']
    end
    categories = categories.flatten.compact
    categories = categories.group_by(&:downcase).map {|k,v| [k, v.length]}    
    categories.sort_by! {|x| x[1]}
    Dir.glob("blog/categories/*").each {|f| File.delete(f)}
    categories.each do |category, count|      
      colour = case count
      when 0..1
        :red
      when 2
        :yellow
        
      else
        :green
      end
      puts "#{category}: #{count}".colorize(colour)
      if category.include?(" ")
        puts "ignoring #{category}: it's stupid".colorize(:red)
      else
        File.open("blog/categories/#{category}.html", "w") do |f|
          f.write <<-EOF
---
layout: archive
title: "Blog Archive: #{category.capitalize}"
tag: #{category}
---
          EOF
        end
      end
    end
  end
end