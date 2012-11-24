require 'bundler/setup'
require 'octokit'
require 'yaml'

files = Dir.glob('en/**/*.md').sort
files.unshift('en/license.txt')
files.unshift('en/title.txt')
files = files.map { |f| File.expand_path(f) }

desc "Create PDF version of FReePG Guide"
task :pdf => :output_dir do
  sh "cd en && pandoc -S --toc --chapters --template ../template.latex -o ../output/FReePG_Guide.pdf #{files.join(" ")}"
end

desc "Create EPUB version of FReePG Guide"
task :epub => :output_dir do
  sh "pandoc -S --epub-metadata=en/metadata.xml --chapters -o output/FReePG_Guide.epub #{files.join(" ")}"
end

desc "Create ALL versions of FReePG Guide"
task :all => %w(pdf epub)

desc "Remove generated files"
task :clean do
  sh "rm -rf output"
end

task :output_dir do
  sh "mkdir -p output"
end

task :upload => :all do
  version = ENV['VERSION'] || "Development-Snapshot-#{Time.now.utc.to_s.gsub(/\W/, '-')}"
  pdf_version = "output/FReePG_Guide-#{version}.pdf"
  epub_version = "output/FReePG_Guide-#{version}.epub"
  sh "cp output/FReePG_Guide.pdf #{pdf_version}"
  sh "cp output/FReePG_Guide.epub #{epub_version}"
  github = YAML.load_file('.github_auth.yml')
  p github
  client = Octokit::Client.new(:login => github['username'],
                               :oauth_token => github['oauth_token'])
  client.create_download('jwilger/freepg_guide', pdf_version,
                         :content_type => "application/pdf")
  client.create_download('jwilger/freepg_guide', epub_version,
                         :content_type => "application/xhtml+xml")
end
