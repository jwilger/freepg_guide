files = Dir.glob('en/**/*.md').sort
files.unshift('en/license.txt')
files.unshift('en/title.txt')

images = Dir.glob('en/**/*.png')

desc "Create PDF version of FReePG Guide"
task :pdf => [:output_dir, :single_file] do
  sh "cd tmp && pandoc -S --toc --chapters --template ../template.latex -o ../output/FReePG_Guide.pdf single_file.md"
end

desc "Create EPUB version of FReePG Guide"
task :epub => [:output_dir, :single_file] do
  sh "cd tmp && pandoc -S --epub-metadata=../en/metadata.xml --chapters -o ../output/FReePG_Guide.epub single_file.md"
end

task :single_file do
  sh 'rm -rf tmp'
  sh 'mkdir -p tmp'
  sh 'touch tmp/single_file.md'
  files.each do |f|
    sh "cat #{f} >> tmp/single_file.md"
    sh "echo " " >> tmp/single_file.md"
  end
  images.each do |i|
    sh "cp #{i} tmp/"
  end
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
