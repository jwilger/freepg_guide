files = Dir.glob('en/**/*.md').sort
files.unshift('en/license.txt')
files.unshift('en/title.txt')

desc "Create PDF version of FReePG Guide"
task :pdf => :output_dir do
  sh "cd en pandoc -S --toc --chapters --template ../template.latex -o ../output/FReePG_Guide.pdf #{files.join(" ")}"
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
