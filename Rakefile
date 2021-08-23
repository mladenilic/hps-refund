require 'hps'

task :refund, [:transaction_id, :amount] do |_, args|
  amount = args[:amount].to_f
  transaction_id = args[:transaction_id]

  Hps.configure do |config|
    config.secret_api_key = ENV['HEARTLAND_API_KEY']
    config.developer_id = ENV['HEARTLAND_DEVELOPER_ID']

    config.version_number = '4307'
    config.service_uri = 'https://cert.api2.heartlandportico.com'
  end

  service = Hps::HpsChargeService.new
  response = service.refund_transaction(amount, 'usd', transaction_id)

  puts response.inspect
end